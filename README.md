docker run/
 --name postgres /
 -e POSTGRES_USER=ericgomes /
 -e POSTGRES_PASSWORD=12345
 -e POSTGRES_DB=heroes /
 -p 5432:5432 /
 -d /
 postgres


 docker psc

docker run /
 --name adminer /
 -p 8080:8080 /
 --link postgres:postgres /
 -d /
 adminer

docker run --name adminer -p 8080:8080 --link postgres:postgres -d adminer


## --- MONGODB
docker run --name mongodb -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=senhaadmin -d mongo:4

docker run --name mongoclient -p 3000:3000 --link mongodb:mongodb -d mongoclient/mongoclient

docker exec -it mongodb mongo --host localhost -u admin -p senhaadmin --authenticationDatabase admin --eval "db.getSiblingDB('herois').createUser({user: 'ericgomes', pwd: 'minhasenhasecreta', role: [{role: 'readWrite', db: 'herois'}]})"