FROM 0caf28170e3b
MAINTAINER Liu Hengyu <18859275929@163.com>


ENV	DEBIAN_FRONTEND noninteractive

RUN	apt-get update -y && apt-get install -y \
	openssh-server xfce4 xfce4-goodies x11vnc sudo bash xvfb && \
	useradd -ms /bin/bash ubuntu && echo 'ubuntu:ubuntu' | chpasswd && \
	echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers && apt-get clean && \
	rm -rf /var/lib/apt/lists/*

COPY 	x11vnc /etc/init.d/
COPY 	xvfb /etc/init.d/
COPY ./entrypoint.sh /tmp
COPY ./vnc.sh /tmp

RUN 	sudo chmod +x /etc/init.d/*

EXPOSE 	5900

ENTRYPOINT ["/tmp/entrypoint.sh"]
