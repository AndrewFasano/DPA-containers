# Dynamic Program Analysis Containers
This is a small collection of dockerfiles to build various dynamic program analysis tools and frameworks.

# Building
To build a container in `dir_name` and call it `name`:
```
docker build -t [name] -f [dir_name]/Dockerfile [dir_name]
```

For example:
```
docker build -t my_dynamorio -f dynamorio/Dockerfile dynamorio
```

Then run the container with:
```
docker run --rm -it my_dynamorio
```

# Upcoming Changes
* More frameworks and tools
* Eventually some CI/CD to build and push containers to dockerhub
