# CloudAcademy + DevOps
This is part of the [CloudAcademy](https://cloudacademy.com/library/) Kubernetes/React/Go/MongoDB Learning Path!

* https://github.com/cloudacademy/voteapp-frontend-react
* https://github.com/cloudacademy/voteapp-api-go
* https://github.com/cloudacademy/voteapp-k8s

# Background
Provides a web based frontend written in React. The web application provides a programming language voting feature where end users can vote for 1 of 3 languages (Go, Java, and NodeJS). The React based web application is designed to be compiled and containerised, and eventually deployed into a Kubernetes cluster, exposed using an Ingress Controller. The web application generates AJAX requests which are sent to a publicly exposed API hosted on the same Kubernetes cluster. The API is written in Go and reads/writes to a MongoDB database, also hosted on the same Kubernetes cluster using a StatefulSet setup.

![Language Vote Application](/doc/voteapp.png)
Steps for building Docker image
0. Ensure node.js is installed to run yarn install and build commands; 
    NOTE: Not sure best way to proceed as my installer is Mac Os
    curl "https://nodejs.org/dist/latest/node-${VERSION:-$(wget -qO- https://nodejs.org/dist/latest/ | sed -nE 's|.*>node-(.*)\.pkg</a>.*|\1|p')}.pkg" > "$HOME/Downloads/node-latest.pkg" && sudo installer -store -pkg "$HOME/Downloads/node-latest.pkg" -target "/"
0. Ensure yarn is installed; run following curl command;
    curl -o- -L https://yarnpkg.com/install.sh | bash
1. Install yarn running command below; Dependency on having yarn installed
    yarn install
2. Set REACT_APP_APIHOSTPORT to local machine in .env file
    REACT_APP_APIHOSTPORT=localhost:8080
3. Perform build running comman below
    yarn build
4. Build the docker image using command below
    docker build -t voteapp/frontend-react:v1 .

