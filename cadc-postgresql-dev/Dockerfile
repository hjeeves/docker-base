FROM centos:7 

# install required software
RUN yum update -y

# repositories and keys
RUN yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
    && rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
RUN yum install -y https://download.postgresql.org/pub/repos/yum/10/redhat/rhel-7-x86_64/pgdg-centos10-10-2.noarch.rpm \
    && rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-PGDG

# packages
RUN  yum -y install postgresql10-server-10.9-1PGDG.rhel7 postgresql10-contrib-10.9-1PGDG.rhel7 postgresql10-devel-10.9-1PGDG.rhel7

# CADC build of pgsphere for postgresql10-server
RUN yum -y install https://www.cadc-ccda.hia-iha.nrc-cnrc.gc.ca/software/pgsphere10-1.1.5-1.el7.centos.x86_64.rpm

RUN yum clean all

RUN mkdir -p /logs
COPY src/init/* /var/lib/pgsql/10/

COPY src/cadc-dev-postgresql-start /usr/bin/
CMD ["/usr/bin/cadc-dev-postgresql-start"]

