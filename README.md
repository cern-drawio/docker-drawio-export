# Drawio Export Server

Dockerfile that installs all the dependencies and runs the [PDF/PNG export server](https://github.com/cern-drawio/draw-image-export2)

## Openshift deployment

> The OpenShift CLI [okd](https://openshift.cern.ch/console/command-line) is needed

Login to your account

```bash
oc login https://openshift.cern.ch --token=<token>
```

Select the project

```bash
oc project <project name>
```

Create the application

```bash
oc new-app . --strategy=docker
```
> The repository specified in the OpenShift build bust be HTTPS

Expose the service

```bash
oc expose svc/<app-name>
```

Enable HTTPS redirection
1. Enter Applications > Routes
2. Select the route to be modified
3. Actions > Edit (top right)
4. Mark "Secure route"
5. Set "Insecure Traffic" to "Redirect"