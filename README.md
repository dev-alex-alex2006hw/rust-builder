Tools built with Ansible to produce portable Rust binaries for Linux, Mac and
Windows. Other platforms on which SSH can be installed should also work.

The principal problem solved by this repo is: "I wrote an application in Rust
and I want to provide binaries that will work on most systems."

The approach taken here is to spin up SSH into designated worker machines,
install Rust, compile binaries and copy them to some other machine. Each worker
machine represents a target.

In order for this process to be generally applicable, it must be configurable.
At least initially, it will be configurable to the extent that **my own** needs
require it. I am not opposed to expanding the configuration, but probably won't
do it unprovoked.

Cross compilation is an alternative solution to this problem, but I've found it
too difficult to achieve. In particular, I could not get cross compilation from
Linux to Mac to work. (My solution was to buy a Mac mini, which is one of the
worker boxes I use with this repo.) However, one thing this repo solves that
cross compilation does not solve (I think) is linking against older versions of
glibc. In particular, one of my worker boxes is Centos 5.11.

There are a variety of other solutions to this problem (e.g., local VMs or
Docker?). It's not clear to me that this repo represents the best solution, but
it appealed to me and I wanted to at least experiment with it.
