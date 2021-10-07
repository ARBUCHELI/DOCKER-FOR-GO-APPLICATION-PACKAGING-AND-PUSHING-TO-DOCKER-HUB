# DOCKER-FOR-GO-APPLICATION-PACKAGING-AND-PUSHING-TO-DOCKER-HUB

##DOCKER COMMANDS:

(Don't forget to navigate to the directory that contains the app and the docker file when using the Docker App):

* docker build -t go-helloworld .
* docker images
* docker run -d -p 6111:6111 go-helloworld
* docker ps
* docker tag go-helloworld rothwulf/go-helloworld:v1.0.0
* docker push rothwulf/go-helloworld:v1.0.0

## IMPORTANT:
* Edit the app on this way:

```
package main

import (
    "fmt"
    "net/http"
)

func helloWorld(w http.ResponseWriter, r *http.Request){
    fmt.Fprintf(w, "Hello World")
}

func main() {
    http.HandleFunc("/", helloWorld)
    http.ListenAndServe(":6111", nil)
}
```

* Edit the dockerfile on this way:
    
```
FROM golang:alpine
LABEL maintainer="Andres R. Bucheli"

WORKDIR /go/src/app

ADD . .

RUN go  mod init

RUN go build  -o helloworld

EXPOSE 6111

CMD ["./helloworld"]
```

THE LAST POINT TO TAKE INTO CONSIDERATION:
Check what IP you got for DOCKER_HOST after running the above command(default is 192.168.99.100:2376)

In browser type whatever IP you got for DOCKER_HOST along with port 5000 Ex: http://192.168.99.100:5000/
