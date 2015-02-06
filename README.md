## docker-kvm-modernie

Package up the modern.ie windows images to be run using kvm via a docker container

Current modern.ie build: _20141027_

This repo triggers a number of autobuild images on Docker Hub under [ianblenke/kvm-modernie](https://registry.hub.docker.com/u/ianblenke/kvm-modernie)

One way you might right run these would be:

    docker run --rm --privileged --name=win10-ie11 -p 5901:5901 -p 3389:3389 -ti ianblenke/kvm-modernie:win10_ie11

The key here being `--privileged` to allow access to /dev/kvm on the docker host, a published port for VNC access on 5901, and a tty for the qemu console prompt.

While that qemu console prompt need not be interactive, it wouldn't hurt to float that in screen/tmux, which are now part of the Dockerfile.
This will be the default CMD behavior shortly.

If you expose a `SPICE` environment variable, you can use a spice client instead of VNC to connect. This will require qxl drivers to be loaded in the guest, however.

You can also pass the qemu-system-x86_64 runtime and arguments after the image, and they will be eval'ed and used instead.

There are definitely opportunities for improvement here.

The next major step is to figure out a way to automate the slipstreaming of the virtio, qxl, and vdagent drivers during the build process.
The boot time with modern.ie without virtio is downright glacial (an hour isn't uncommon).

Worst case, you can build a Dockerfile that references these as a FROM and script the startup yourself.

