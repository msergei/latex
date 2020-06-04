# Sharelatex full with docker-compose

ShareLatex with all packages include pythonhighlight. You can start it in amd64 by docker-compose.

## How to install?

1.Install docker and docker-compose (tested on docker version > 18 and docker-compose version > 1.24)

2.Start build and up services in folder project:
```docker-compose up -d```

3.Get url for set password for your user by command (in folder project):
```docker-compose exec web /bin/bash -c "cd /var/www/sharelatex; grunt user:create-admin --email=joe@dou.com"``` 

4.Open in browser url from 3. to set password.

5.Login with email and your pass.

# How to compile .tex without start web server?

In folder with .tex files you need execute (do not forget change main.tex to you filename):

```
docker run --rm -it --user="$(id -u):$(id -g)" --net=none --entrypoint=bash -v "$PWD":/source_files cemulate/sharelatex-full:v1.2.1 -c "cd /source_files && pdflatex main.tex && pdflatex main.tex"
```