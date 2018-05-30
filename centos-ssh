From centos:latest

RUN yum -y install openssh-server openssh-clients \
    && ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N "" \
    && ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N "" \
    && ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key -N "" \
    && sed -i 's#UsePAM yes#UsePAM no#g' /etc/ssh/sshd_config \
    && echo "123456" | passwd --stdin root \
    && yum clean all \
    && rm -rf /var/cache/yum/ \
    && history -c

EXPOSE 22

CMD ["/usr/sbin/sshd","-D"]
