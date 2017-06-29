# Using logstash examples

## Run examples

##### You will need to change the paths to relate to where you save examples

Choose the required example 

config_1 - writes the contents of app.log to console
config_2 - writes the contents of app.log to out.log file
config_3 - converts the contents of app.log using a grok template to out.log file

* (from command prompt in C:\DevTools\logstash-5.4.2\bin) logstash -f config_[version].json e.g. logstash -f config_3.json

### Clear the way logstash remembers how much of a file has been read (for testing)

* [logstash-directory]\data\plugins\inputs\file
* Remove the .sincedb file
