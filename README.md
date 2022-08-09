# knative-serving-quarkus-demo

This demo shows how to serve a Java application on Knative using Quarkus.

## Requirements

* A local Kubernetes cluster with a running Knative Serving cluster.
* `kn` CLI installed. See [Knative CLI tools](https://knative.dev/docs/client/#kn).
* JDK 11+ installed with JAVA_HOME configured appropriately
* Apache Maven 3.8.1+

## Deploying the application

```shell
mvn package -Dquarkus.kubernetes.deploy=true
```

## Listing the deployed services

```shell
kn service list
```

Output:

```shell
NAME                           URL                                                                   LATEST                               AGE   CONDITIONS   READY   REASON
knative-serving-quarkus-demo   http://knative-serving-quarkus-demo.default.10.106.207.219.sslip.io   knative-serving-quarkus-demo-00001   17s   3 OK / 3     True
```

Use the returned URL to access the deployed application.

## Sending a request to the deployed service

```shell
curl -X 'GET' '${URL}' -H 'accept: text/plain'
```

Replace `${URL}` with the URL of the deployed service.

Output:

```shell
Hello from RESTEasy Reactive
```

------------

This project uses Quarkus, the Supersonic Subatomic Java Framework.

If you want to learn more about Quarkus, please visit its website: https://quarkus.io/ .