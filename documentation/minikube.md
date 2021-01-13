# Minikube Documentation

Weather-service and traffic-service, should be run in a minikube. 
Installation guide for minikube: https://v1-18.docs.kubernetes.io/docs/tasks/tools/install-minikube

First of all we need the .yaml files for both services we want to run there:
![traffic-service](../traffic-service.yml)
![weather-service](../weather-service.yml)


One important step is now to make sure we do the authentification right, because we had a lot of problems with not having persmission to / not finding the repository on docker hub.
We can find the config.json under C:\Users\<User>\.docker and there we need to execute the following command:

kubectl create secret docker-registry regcred --docker-server=https://index.docker.io/v1/ --docker-username=<your-name> --docker-password=<your-pword>

Once done you can check the outcome with:

kubectl get secret regcred --output=yaml
