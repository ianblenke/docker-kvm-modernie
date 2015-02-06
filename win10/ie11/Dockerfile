FROM ianblenke/kvm

RUN apt-get -y update
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install curl git wget libguestfs-tools aria2 unzip dos2unix unrar-free wget git alien samba xorriso screen

WORKDIR /data

RUN git clone https://github.com/ianblenke/ie-vm.git

WORKDIR /data/ie-vm

RUN ./fetch.sh $(./ie-urls.sh | grep -i win10 | grep -i ie11)

# Grab the virtio driver ISO at build time
RUN wget -c --recursive --no-directories --accept-regex 'virtio.*\.iso' \
        http://alt.fedoraproject.org/pub/alt/virtio-win/stable/

CMD ./start.sh disk.qcow2
