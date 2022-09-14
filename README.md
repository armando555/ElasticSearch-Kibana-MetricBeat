# ElasticSearch-Kibana-MetricBeat
 this project is a docker-compose deployment for analize metrics of hardware in a machine
# Execute the docker-compose
```
docker-compose up -d
```

## connect to the docker elasticsearch
```
docker exec -it elasticsearch bash
```

## execute bin and set a password for the different users
For testing set all passwords with the value of "12345678" if you are going to do a serious deployment set a good password and use that password in metricbeat.yml replacing 12345678 with the goodpassword and that's all.
```
. /usr/share/elasticsearch/bin/elasticsearch-setup-passwords interactive
```

# Configure the MetricBeat
Follow the installation guide for your respective operating system
## NOTE: READ THIS PLEASE IS VERY IMPORTANT
This version the kibana and elasticsearch only work with metricbeat 7.10.1 version

## Windows
Go to this link https://www.elastic.co/downloads/past-releases/metricbeat-7-10-1  and download the windows versión in ZIP extension
```
https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.10.1-windows-x86_64.zip
```
Now, Extract the contents of the zip file into C:\Program Files.


Rename the metricbeat-<version>-windows directory to Metricbeat.

## Important: 
Move the file "metricbeat.yml" that is here in the repo to this directory of Metricbeat and replace the default file that this directory has.


## Installation:

Open a PowerShell prompt as an Administrator (right-click the PowerShell icon and select Run As Administrator).


Now run this two commands to go to the folder and install MetricBeat service
```
cd 'C:\Program Files\Metricbeat'
```
```
.\install-service-metricbeat.ps1
```
After that, we are going to list the modules and enable the windows module to upload all the hardware data to kibana that is capturated for the OS
```
.\metricbeat.exe modules list
```
```
.\metricbeat.exe modules enable windows
```
Finally, setup it and start the service
```
.\metricbeat.exe setup -e
```
```
Start-Service metricbeat
```

# Results
Open this URL http://localhost:5601/ login with the username: "elastic" and password "12345678", and open the dashboard called "[Metricbeat System] Overview ECS"


# GUIDE
```
https://www.elastic.co/guide/en/beats/metricbeat/current/metricbeat-installation-configuration.html
```

