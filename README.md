# Elasticsearch, Logstash, Kibana (ELK) Docker image


This Docker image provides a convenient centralised log server and log management web interface, by packaging Elasticsearch, Logstash, and Kibana, collectively known as ELK.

Forked from [https://github.com/spujadas/elk-docker](https://github.com/spujadas/elk-docker) and adapted for diferent uses.

### Please ensure you're in the correct branch !!

## quorum branch 

Get to the correct branch
```
git checkout quorum
```

Update
```
git pull
```

### Quorum Log configuration

Make sure you set the volume paths correctly to your host paths in **docker-composer.yml**, this is an example for a linux environment.

```
  volumes:
    ## Elasticsearch mapped volume for persistent data
    - /home/<user>/tmp/elk-data:/var/lib/elasticsearch
    
    ## Directory where logs to be analyzed are stored
    - /home/<user>/alastria/logs/:/var/log/alastria
```

**/var/lib/elasticsearch/** is where elasticsearch will store it's data, map it to an external volume or a docker volume if you want to keep the data on restarts.

Logstash is configured to read **/var/log/alastria/quorum_YYYY-mm-dd.log** files by default, if you want to change the path or filenames, edit **./conf.d/10-quorum.conf** and rebuild the project.
You can also log into the running container and edit 

```/etc/logstash/conf.d/10-quorum.conf``` 

Logstash will restart your configuration changes after 10 seconds.

If the system is not indexing after a restart, try to remove 

```
/opt/logstash/data/plugins/inputs/file/.sincedb_xXxxXxxXXXxxXxxXXXxxXxXxxXX
```

#### Checks and configurations for quorum.

The project is meant to work automatically to read quorum logs.
Once everything is up, you can check on Kibana **http://localhost:5601** if everything is fine.

First go to *dev tools* section and check if there are indices ongoing

	GET _cat/indices?pretty

If quorum_YYYY-mm-dd is available, get to Manage section and create the Index-Pattern.

Then go to *Saved Objects* and **import** *templates/quorum_searches.json*

Now you'll have some saved searches and graphs.

###  Build with:

```
docker-compose -p <project-name> build 
```

### Run with:

```
docker-compose -p <project-name> up 
```


### Documentation

See the [ELK Docker image documentation web page](http://elk-docker.readthedocs.io/) for complete instructions on how to use this image.


### About

Branch Written by [Jacinto Calvo](https://seriousman.org), released under the [Apache 2 license](https://www.apache.org/licenses/LICENSE-2.0).

