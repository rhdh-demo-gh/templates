# Deploy Component Documentation

At $COMPANY_NAME we're enabling developer self-service by standardizing our
deployment practices for all new software components. 

## Usage

Assuming you've already created a new software component using one of our
helpful templates, this template will allow you to raise a request to deploy
it in one of our environments by providing just two pieces of information:

1. The Component you wish to deploy.
1. The target environment, e.g development or production.

Running this template opens a Pull Request (PR) in the [app-of-apps](https://github.com/rhdh-demo-gh/app-of-apps)
repository requesting the creation of the deployment.

Your Component will be deployment PR will either be approved or denied by a
member of the operations or platform engineering team. 

## Approval Times

* Development: <1 day
* Production: 1 week (pending security review requirements)