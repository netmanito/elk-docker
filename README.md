# Elasticsearch, Logstash, Kibana (ELK) Docker image

[![](https://badge.imagelayers.io/sebp/elk:latest.svg)](https://imagelayers.io/?images=sebp/elk:latest 'Get your own badge on imagelayers.io') [![Documentation Status](https://readthedocs.org/projects/elk-docker/badge/?version=latest)](http://elk-docker.readthedocs.io/?badge=latest)

This Docker image provides a convenient centralised log server and log management web interface, by packaging Elasticsearch, Logstash, and Kibana, collectively known as ELK.

Forked from [https://github.com/spujadas/elk-docker](https://github.com/spujadas/elk-docker) and adapted for personal uses.

###  Build with:

```
docker build -t <repo-user>/elk .
```

### Run with:

```
docker run -p 5601:5601 -p 9200:9200 -p 5044:5044 -it --name elk <repo-user>/elk
```

### Documentation

See the [ELK Docker image documentation web page](http://elk-docker.readthedocs.io/) for complete instructions on how to use this image.


### About

Written by [Sébastien Pujadas](https://pujadas.net), released under the [Apache 2 license](https://www.apache.org/licenses/LICENSE-2.0).

