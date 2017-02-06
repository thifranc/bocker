FROM ubuntu:16.04

RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd
#RUN sed -ie 's/#   Port 22/#   Port 42/g' /etc/ssh/ssh_config

EXPOSE 22
COPY ./id_rsa.pub /root/.ssh/authorized_keys
#CMD service ssh start && while true; do sleep 3000; done
CMD ["/usr/sbin/sshd", "-D", "-E", "/root/logFile", "-p", "42"]
