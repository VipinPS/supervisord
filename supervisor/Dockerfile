FROM ubuntu
MAINTAINER eyslides@gmail.com
RUN apt-get update
RUN apt-get install -y openssh-server apache2 supervisor
RUN mkdir -p /var/lock/apache2 /var/run/apache2 /var/run/sshd /var/log/supervisor
RUN cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
RUN chmod a-w /etc/ssh/sshd_config.backup
RUN mkdir /var/run/sshd
RUN echo 'root:screencast' | chpasswd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
EXPOSE 22 80
CMD ["/usr/bin/supervisord"]
