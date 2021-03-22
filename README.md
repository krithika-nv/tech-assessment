# tech-assessment

### Short description: 
golang-sorting-webapp is a dockerized Golang web application deployable on Kubernetes using Helm. This web application sorts incoming https requests based on header names. It is also integrated with Prometheus to provide _number_of_requests_ custom metric to count the number of incoming https requests. 

### Software used to build this prototype:
1. go1.16
1. LibreSSL 2.6.5
1. Docker engine 20.10.5
1. kubectl (client version: v1.19.7, server version: v1.20.2)
1. minikube version: v1.18.1
1. Helm version: v3.5.3

### Notes to the reviewer:
1. This repo contains: 
	1. webapp go code, server secrets and other dependencies 
	1. Dockerfile used to create the docker image of the app 
	1. Helm yaml files 
	1. Helm test suite  
	1. Helm install notes
1. Name of the expected Prometheus metric is _number_of_requests_.
1. This is a https webapp.
1. Helm install notes has more info about accessing the app and prometheus endpoints.
1. This prototype was tested on macOS only.
1. To maintain simplicity, no user/service accounts are available. 

### Basic Tests:
1. Basic Helm Hook test and Helm Linting.
1. Functionality and compatibility testing on Google Chrome, Safari and Firefox browsers - working as expected.
1. Basic performance analysis: On an average for 2241 hits/s and 20 virtual users: 
	1. Response time: 34ms 
	1. Time to First Byte: 8ms
	1. DOM Content Loading: 12ms
	1. DOM Processing: 20ms
1. Basic security testing on the app endpoint:
	1. The connection to this site is encrypted and authenticated using TLS 1.3, X25519, and AES_128_GCM.
	1. All resources on this page are served securely.
	1. This site is missing a valid, trusted certificate (net::ERR_CERT_AUTHORITY_INVALID). This is because it is self-signed. 
1. Chrome's lighthouse testing.

### Scope for improvement:
1. Integration with Fluentd and Elasticsearch for better logging.
1. Integration with Postgres majorly for data collection from Prometheus.
1. Include loadbalancing.
1. More efficient test suites.
1. Better ways to store and access secrets.
1. Follow best practices for storing secrets and certificates.
1. CI/CD pipeline for this build, using GitHub Actions.
