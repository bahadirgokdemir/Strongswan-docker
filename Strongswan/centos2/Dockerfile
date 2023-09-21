FROM centos:8
RUN echo "sslverify=false" >> /etc/yum.conf
RUN echo " net.ipv4.ip_forward = 1  " >> /etc/sysctl.conf
RUN echo " net.ipv4.conf.all.accept_redirects = 0   " >> /etc/sysctl.conf
RUN echo " net.ipv6.conf.all.forwarding = 1    " >> /etc/sysctl.conf
RUN echo " net.ipv4.conf.all.send_redirects = 0    " >> /etc/sysctl.conf


RUN cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*

RUN echo "sslverify=false" >> /etc/yum.conf

RUN yum -y update --setopt=sslverify=false

RUN dnf -y install epel-release 
#RUN dnf -y install strongswan-starter
RUN dnf -y install strongswan
RUN systemctl enable strongswan-starter

CMD ["strongswan-starter", "start"]

#CMD ["tail", "-f", "/dev/null"]

#CMD ["executable"]
