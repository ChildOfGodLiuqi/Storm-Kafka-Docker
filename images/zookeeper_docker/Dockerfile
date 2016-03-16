FROM ubuntu:trusty
RUN apt-get update && apt-get dist-upgrade -y
RUN apt-get install -y zookeeper
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
COPY zoo.cfg /etc/zookeeper/zoo.cfg
COPY start.sh /usr/local/bin/start.sh
RUN sed -i 's/ROLLINGFILE/CONSOLE/' /etc/zookeeper/conf/environment
# Fix DNS resolution issues when nss is not installed 
RUN echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf
# Set DNS cache to 10 seconds (Cache is permanent by default). Network hosts are volatile in Docker clusters.
RUN grep '^networkaddress.cache.ttl=' /etc/java-7-openjdk/security/java.security || echo 'networkaddress.cache.ttl=10' >> /etc/java-7-openjdk/security/java.security
ADD start.sh /usr/local/bin/
CMD ["/usr/local/bin/start.sh"]
