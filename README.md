

# Project1
-----------------------


## Github project

Project url

https://github.com/sagar-iitg/Jenkins-Project-Django.git/

## Source Code Management
Repositories
Repository URL


https://github.com/sagar-iitg/Jenkins-Project-Django.git


## Build Triggers

### GitHub hook trigger for GITScm pollin

## Build Steps

Execute shell
```
echo "Building"
docker-compose down
docker-compose up -d --no-deps --build web
```
