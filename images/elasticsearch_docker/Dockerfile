FROM elasticsearch:1.7.4
MAINTAINER Gary Liu <gary_liu@mail.pic.net.tw>
#RUN mkdir /usr/share/elasticsearch/bin/data
#RUN chown -R elasticsearch:elasticsearch /usr/share/elasticsearch/bin/data
RUN gosu elasticsearch /usr/share/elasticsearch/bin/plugin --install mobz/elasticsearch-head
#RUN gosu elasticsearch /usr/share/elasticsearch/bin/plugin install elasticsearch/marvel/latest
RUN gosu elasticsearch /usr/share/elasticsearch/bin/plugin --install lukas-vlcek/bigdesk
#RUN gosu elasticsearch /usr/share/elasticsearch/bin/plugin install elasticsearch/elasticsearch-lang-groovy/2.0.0
