
## Acme Air Customer Service - Java/Liberty 
### JDBC (DB2 for i) version 

An implementation of the Acme Air Customer Service for Java/Liberty. The primary task of the customer service is to store, update, and retrieve customer data on Db2 for i. It can be adapted for any jdbc based database server.  Fork from the Mongodb based [Customer Service](https://github.com/blueperf/acmeair-customerservice-java).  

Db2 for i is a rock solid database server with HA and DR capabilities. This example shows you how to intgrate the Kubernetes and Stateless world with the statefull and transactional world on IBM i. 

## Build Instruction for OpenShift 

- First git clone this repository, in addition to the other microservices from the [BluePerf project](https://github.com/blueperf/acmeair-mainservice-java). Test branch : branch microprofile-3.3 
- Download and Copy an up to date jdbc driver in the drivers folder. ex: jt400.jar
- Use the scripts in the driver folder to create the acmeair database and import the initial data.
- Install maven, oc cli , docker or podman client first. Refer to the original BluePerf project instructions. 
- Follow the instruction on BluePerf to build the other microservices.
- Build and deploy this micro-service (replacing the initial [Customer Service](https://github.com/blueperf/acmeair-customerservice-java) by this Db2 for i alternative from in a single command using the following commands. 
Note: Default user profile is acmeair , password is password, library (sql collection) is acmeair
Feel free to update the Deployment environment variable values according to your environement (user, password, lib list)

- $ export DB2FORI_HOSTNAME=bendemo.10.7.19.71.nip.io
- $ cd scripts
- $ ./buildAndDeployToOpenshift-CustomerService.sh  default-route-openshift-image-registry.apps-crc.testing/acmeair image-registry.openshift-image-registry.svc:5000/acmeair acmeair-acmeair.apps-crc.testing docker open-liberty:full 