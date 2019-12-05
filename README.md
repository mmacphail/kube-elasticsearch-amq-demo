<h1 align="center">Welcome to kube-elasticsearch-amq-demo 👋</h1>
<p>
  <a href="#" target="_blank">
    <img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-yellow.svg" />
  </a>
  <a href="https://twitter.com/MalcMacphail" target="_blank">
    <img alt="Twitter: MalcMacphail" src="https://img.shields.io/twitter/follow/MalcMacphail.svg?style=social" />
  </a>
</p>

> Example project to deploy an ELK stack to kubernetes

## Dependencies

This project requires the [activemq-logstash](https://github.com/mmacphail/activemq-logstash-docker-image) github package docker image. To allow minikube to download the docker image, configure it:

    kubectl create secret generic pullsecret \
        --from-file=.dockerconfigjson=${HOME}/.docker/config.json \
        --type=kubernetes.io/dockerconfigjson
    kubectl patch serviceaccount default -p '{"imagePullSecrets": [{"name": "pullsecret"}]}'

The docker token must be set in the config.json file. This can be done when [authenticating to github packages](https://help.github.com/en/github/managing-packages-with-github-packages/configuring-docker-for-use-with-github-packages#authenticating-to-github-packages).

See this [article](https://markuscisler.com/minikube-private-registry/) for more explanations.

## Configuration

Minikube requires some tweaking to run this example. I like space, so I run 16Gi of RAM, but feel free to adjust accordingly  to your specs:

    minikube config set memory 16000

Minikube will pull the image from [activemq-logstash]() github docker package.


## Deployment
Deploy on minikube using kubectl:

    kubectl apply -f es.yaml,kibana.yaml,amq.yaml,logstash.yaml

## Author

👤 **mmacphail**

* Twitter: [@MalcMacphail](https://twitter.com/MalcMacphail)
* Github: [@mmacphail](https://github.com/mmacphail)

## Show your support

Give a ⭐️ if this project helped you!

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_
