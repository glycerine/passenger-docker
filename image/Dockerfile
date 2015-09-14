FROM phusion/baseimage:0.9.17
MAINTAINER Phusion <info@phusion.nl>

ADD extra/nsq-0.3.5.linux-amd64.go1.4.2/bin/ /usr/bin/
ADD extra/go1.4.2.linux-amd64                 /usr/local/
ADD extra/go1.4.2.linux-amd64/go/bin/        /usr/bin/
ADD extra/src /usr/

ADD . /pd_build

RUN /pd_build/install.sh

# enable sshd with insecure key
RUN rm -f /etc/service/sshd/down
RUN /etc/my_init.d/00_regen_ssh_host_keys.sh
RUN /usr/sbin/enable_insecure_key

CMD ["/sbin/my_init"]
EXPOSE 80 443 4150 4151 4160 4161 4170 4171
