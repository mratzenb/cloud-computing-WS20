# Project Proposal: Breaking a "Monolith"

## Current state:
Currently, there exists a Spring-Boot Application written in Java that provides two "Services" to a Frontend which is written in Angular.

   1. It provides the current weather and a weather forecast based on a given city and the amount of forecast days.
   2. It provides traffic information that gets scraped from [ö3](https://oe3.orf.at/verkehr/).
   
These two services then get compiled and packaged into a single application. This also is the problem, because everytime a service changes a little bit, the entire application needs to be redeployed (which is actually not that big of a problem because the program is very small).

## What should be done
The goal of this project would be to break the "Monolith" and create a Mircoservice for each of the two backend services.  \
These two microservices should then be running inside a docker container and should be managed via kubernetes. For kubernetes Microsoft Azure or kind will be used.

The ultimate goal would be that the already existing Frontend is able to get the data from the Microservices. 

## Open questions
* Shall the frontend directly call Microsoft Azure or is it better to provide a backend endpoint which then calls the Microserivce. If the latter is used the frontend still calls the backend via localhost (which it does currently) and the backend then calls the Microservice instead of performing the task on its own.
