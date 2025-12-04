# Download system packages (rpm or deb) needed by 'kubeasz'
# @author:  gjmzj
# @repo:    https://github.com/easzlab/dockerfile-kubeasz-sys-pkg
# @ref:     https://github.com/easzlab/kubeasz

FROM ubuntu:22.04 as downloader

RUN apt update && \
    apt install -d -y \
      conntrack \
      ipset \
      ipvsadm \
      jq \
      libseccomp2 \
      lvm2 \
      nfs-common \
      rsync \
      socat iptables sshpass linux-image-5.15.0-153-generic linux-headers-5.15.0-153-generic linux-modules-5.15.0-153-generic linux-modules-extra-5.15.0-153-generic linux-tools-5.15.0-153 build-essential curl git lsb-release snapd unzip vim cmake mbw && \
    cd /var/cache/apt/archives && \
    tar zcvf /tmp/ubuntu_22.tgz *.deb

# storing packages on alpine
FROM alpine:3.16

ENV SYS_PKG_VER=1.0.1

COPY --from=downloader /tmp/*.tgz /packages/

CMD [ "tail", "-f", "/dev/null" ]
