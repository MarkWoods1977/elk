# elk

## Run in docker 

* Use the sebp/elk docker image
* Follow the install in https://elk-docker.readthedocs.io/
* Ensure you set vm.max_map_count=262144 in /etc/sysctl.conf of the host

### running

#### Use docker compose 

`elk:
  image: sebp/elk
  ports:
    - "5601:5601"
    - "9200:9200"
    - "5044:5044"`
	
* save as docker-compose.yml
* sudo docker-compose up elk

### Changing the config in logstash (initally to test witout ssl)

* docker exec -it [docker container name] bash
* cd /etc/logstash/conf.d 
* vi 02-beats-input.conf and set ssl to be false and remove ssl related parameters (its easier to paste change in rather than edit inline)

### Running filebeat forwarder (in windows)

* (from git bash) ./filebeat -c- filebeat.yml -e
* edit filebeat.yml setting [log folder]\*.log in filebeat.prospectus
* set the host as [logstash server]:5044 in output.logstash

### View in Kibana

* In kibana [kibana ip]:5601 go to management -> index patterns -> + -> enter the index name as filebeat-*
* In kibana dicover -> choose index and the logs should appear.
