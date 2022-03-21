QIRA Container
====

This is based off [the Dockerfile provided by Qira](https://github.com/geohot/qira/blob/master/docker/), but can be built without first cloning the repo, has better caching, and fixes a few bugs.


To run:

```
docker build . -t qira
docker run --rm -it -v $(pwd):/host -p3002:3002 qira
```

Then run a process under qira in the guest, e.g., `qira whoami` and view the trace by browsing to `localhost:3002` on your host machine.
