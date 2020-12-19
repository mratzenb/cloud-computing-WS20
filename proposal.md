# Project Proposal: Breaking a "Monolith"

## Current state:
Currently, there exists a Spring-Boot Application written in Java that provides two "Services" to a Frontend which is written in Angular.

   1. It provides the current weather and a weather forecast based on a given city and the amount of forecast days. The data comes from [openweathermap](https://openweathermap.org)
   2. It provides traffic information that gets scraped from [ö3](https://oe3.orf.at/verkehr/).
   
These two services then get compiled and packaged into a single application. This also is the problem, because everytime a service changes a little bit, the entire application needs to be redeployed (which is actually not that big of a problem because the program is very small).

Some more details about the backend implementation:
* _@RestController_ is used for each "Service". The traffic information "Service" has a single endpoint, wheras the weather service has two.
* _@Service_ is used to provide and get the data from the internet.

The original repository can be found [here](https://github.com/mratzenb/smart-mirror-cloud-computing).

## What should be done
The goal of this project would be to break the "Monolith" and create a Mircoservice for each of the two backend services. These two microservices should then be running inside a docker container. ~~and should be managed via kubernetes. For kubernetes Microsoft Azure or kind will be used.~~  
For the application we think it is best to be running locally. Hence, kubernetes will not be needed. Instead, _Kind_ will be used to to manage them locally. \
Additionally, the Angular frontend will also be transformed into some kind of "Microservice". This means, that it will also run inside a Docker container.

~~Instead of kubernetes a Jenkins build server could be used to support Continous Integration.~~ To support continous integration we use Github Actions to build the microservices. Therfore, the backend has to be split up into two seperate repositories to make them build individually. After a successful each microservice gets published to Docker Hub (via Github Actions). This means that overall there will be 3 docker images. 

The ultimate goal would be that the already existing Frontend is able to get the data from these Microservices. 

## Who is doing what
| Member  | Responsibility                                                                         |
| ------- | -------------------------------------------------------------------------------------- |
| Michael | <ul><li>Splitting the Monolith<li>Generate Dockerfiles<li>Generate Github Actions</ul> |
| Nikola  | <ul><li>Generate Github Actions <li>Local _Kind_ deployment</ul>                       |

