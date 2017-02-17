FROM  ubuntu:16.04
ENV   container docker
RUN apt-get update
RUN apt-get install --no-install-recommends --no-install-suggests -y nginx
RUN systemctl enable nginx
STOPSIGNAL SIGRTMIN+3
EXPOSE 80
CMD [ "/sbin/init" ]
