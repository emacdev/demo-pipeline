# OpenShift Contain Platform

 - Installed on top of a 'cluster' of nodes that function as compute platform
 - Can be installed on-prem or on existing cloud platformts
 - Heart of system is wrapping Docker + Kubernetes technologies as a Platform for getting code built, tested, and deployed to market faster
 - Integrated docker registry for all new docker images
 - Can pull docker images from any image stream (configurable)
 - Kubernetes to expose services,   

# Creating a new app

## Create a project

oc new-project myapp --display-name="nodejs-demo" --description="Demo of nodejs app deployed using openshift"

## Create the app directly from the source code

 oc new-app -f C:\env\nodejs-ex\openshift\templates\nodejs.json

## Build the app

oc start-build

## Check the app status

oc status

## Check the logs

oc logs -f bc/nodejs-ex

## Add a route

oc expose svc/nodejs-ex --hostname=localhost

## Add the database

oc new-app centos/mongodb-26-centos7 -e MONGODB_USER=admin,MONGODB_DATABASE=mongo_db,MONGODB_PASSWORD=secret,MONGODB_ADMIN_PASSWORD=super-secret


## Get status

oc status


## Get the url of the database

oc set env dc/nodejs-ex MONGO_URL='mongodb://admin:secret@172.30.54.58:27017/mongo_db

## The above should trigger a build

# Creating a Continuous Integration / Continuous Deployment Pipeline

tg-server build pipeline project with jenkins image deployed
 - Go through pipeline

tg-dev environment which contains first deployment
 - promoto to QA if deployed

tg-test subsequent environment which the latest promoted image is deployed to