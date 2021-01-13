# Minikube Documentation

Weather-service and traffic-service, should be run in a minikube. 
Installation guide for minikube: https://v1-18.docs.kubernetes.io/docs/tasks/tools/install-minikube

First of all we need the .yaml files for both services we want to run there:
![traffic-service](../traffic-service.yml)
![weather-service](../weather-service.yml)

The important part here is:

      containers:
            - name: traffic-service
              image: mratzenb/smart-mirror:traffic-service
              ports:
              - containerPort: 8080
            imagePullSecrets:
              - name: regcred
        
Here we need to specify what image to use. We use the one on out docker-hub with the container port 8080. The last part is important so we actually have access to the repository.
We can find the config.json under C:\Users\<User>\.docker and there we need to execute the following command to get our token:

      kubectl create secret docker-registry regcred --docker-server=https://index.docker.io/v1/ --docker-username=<your-name> --docker-password=<your-pword>

Once done you can check the outcome with:

      kubectl get secret regcred --output=yaml

Once the pods are up and running, the last thing to do is to run the frontend-service:

      docker run -p 4200:80 mratzenb/smart-mirror:frontend-service
