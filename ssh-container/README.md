# SSH Container

This is container which allows ssh connections. This is insecure
so do not use this at the public network. This is only for studying
purposes.

I use this container for Ansible studies and testing. The
passwords at the Dockerfile are not my real passwords and they
are very insecure.

So how to use this?

Build `docker build -t studies .` and run `docker run --rm -d studies`. 
You can see the IP address of the running container with command 
`docker logs <container id>`.

When you take the containers up and down a lot,
at some point you get tired with server side key verification
and errors. I've added following snippet to my _~/.ssh/config_ file:

```config
host 172.*
    UserKnownHostsFile /dev/null
    StrictHostKeyChecking no
```

This disables key checks from all ssh connections to the networks
with 172 prefix. This is insecure practice, so understand what you are 
doing please.
