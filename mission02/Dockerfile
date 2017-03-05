FROM ubuntu:16.04

RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd
#RUN sed -ie 's/#   Port 22/#   Port 42/g' /etc/ssh/ssh_config
RUN useradd -ms /bin/bash thifranc
RUN groupadd sshusers
RUN usermod -a -G sshusers thifranc


#USER thibault
#WORKDIR /thibault

#ENV HOME /thibault

#RUN echo "AllowGroups sshusers" >> /etc/ssh/sshd_config
RUN echo "PubkeyAuthentication yes\nAuthorizedKeysFile .ssh/authorized_keys" >> /etc/ssh/sshd_config

EXPOSE 22
COPY ./id_rsa.pub /root/.ssh/authorized_keys
COPY ./id_rsa.pub /thifranc/.ssh/authorized_keys
#CMD service ssh start && while true; do sleep 3000; done
CMD ["/usr/sbin/sshd", "-D", "-p", "42"]
