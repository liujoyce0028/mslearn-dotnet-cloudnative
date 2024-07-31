# eShopLite
https://learn.microsoft.com/en-us/training/modules/dotnet-microservices/3-exercise-build-docker-image

# Cli:
dotnet publish /p:PublishProfile=DefaultContainer --no-restore

docker images


(not in used)
docker build -t productsbackend:latest -f Products/Dockerfile .

(in used)
docker build -t productsbackend:latest -f Dockerfile .

docker run -it --rm -p 32001:8080  products

docker run -it --rm -p 32001:8080 productsbackend



# check
To test the service, switch to the PORTS tab then, 
to the right of the local address for the Back End port, select the globe icon. 
The browser opens a new tab at that address.
http://localhost:32001/api/product

# Microservices orchestration
## Create a Docker Compose file for orchestration
Build the images and run the containers:  
 use Docker Compose to build and start both front-end and back-end components.
 1. To build the container images us .NET container support, select the Terminal tab, 
and then run the following command: 
 dotnet publish /p:PublishProfile=DefaultContainer --no-restore
 
 2. To start both the front-end website and the back-end web API, run this command:
 docker compose up

 =======================================================================
