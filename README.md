## docker-kvm-modernie

Package up the modern.ie windows images to be run using kvm via a docker container

Current modern.ie build: _20141027_

This repo triggers a number of autobuild images on Docker Hub under [ianblenke/kvm-modernie](https://registry.hub.docker.com/u/ianblenke/kvm-modernie)

One way you might right run these would be:

    docker run --rm --privileged --name=win10-ie11 -p 5900:5900 -p 3389:3389 -ti ianblenke/kvm-modernie:win10_ie11

There are definitely opportunities for improvement here.

Worst case, you can build a Dockerfile that references these as a FROM and script the startup yourself.

