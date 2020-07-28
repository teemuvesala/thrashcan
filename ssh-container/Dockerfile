FROM ubuntu:16.04

RUN apt-get update && apt-get install -y openssh-server sudo iproute2
RUN mkdir /var/run/sshd
RUN echo 'root:THEPASSWORDYOUCREATED' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN adduser tvesala
RUN echo 'tvesala:q1w2e3' | chpasswd
RUN echo 'tvesala ALL=(ALL) NOPASSWD: ALL' >/etc/sudoers.d/tvesala
COPY starter.sh /


# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/starter.sh"]