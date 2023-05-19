FROM ubuntu:latest

RUN apt update && apt install -y \
    git=1:2.34.1-1ubuntu1.8 \
    python3=3.10.6-1~22.04 \
    python3-pip=22.0.2 \
    openssh-server
#RUN sed -i '/PermitRootLogin prohibit-password/c\PermitRootLogin yes' \
#    /etc/ssh/sshd_config

COPY id_rsa.pub /root/.ssh/authorized_keys

COPY requirements.txt .

RUN pip3 install -r requirements.txt

COPY add_host.patch start.sh ./

CMD ["/usr/sbin/sshd" , "ps aux" , "sleep 500"]
