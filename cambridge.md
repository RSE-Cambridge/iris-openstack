# IRIS OpenStack @ Cambridge University

The [Cambirdge University](https://www.hpc.cam.ac.uk/) IRIS OpenStack deployment is part of the [Cumulus](https://www.top500.org/system/179577) supercomputer.

For more details please contact John Taylor, StackHPC.

## Creating your Account

Please vist the OpenStack Horizon Dashboard to login, selecting "Federated Login":
https://cumulus.openstack.hpc.cam.ac.uk/

Due to the use of the EGI IAA development instance, while your instituion may be listed,
it is unlikely to work. Grid certificates and google accounts however do seem to work,
so please use those instead.

Once IRIS's Indigo IAM setup has access to edugain, the hope is to switch all accounts
to that system.

## Getting your Account authorized

While it is hoped Keycloak and/or Indio IAM will eventualy automate the group membership
workflow, this is currently a fairly manual process that can be kickstarted by opening a
bug against this github repository:
https://github.com/RSE-Cambridge/cumulus-config/issues

Please tell us what project you are working on (LSST, Euclid, etc)
and please provide your user name as shown here:
https://cumulus.openstack.hpc.cam.ac.uk/project/api_access/view_credentials/

## Starting your First Server

Please ensure you have an appropriate ssh public key imported here:
https://cumulus.openstack.hpc.cam.ac.uk/project/key_pairs

In the top left, make sure you have the correct project selected,
and not the project called "iris". You will now be able to see all
the resources in the selected project.

Click the "Launch Instance" button at the top right of this page,
picking the smallest flavor and the network "cumulus-internal":
https://cumulus.openstack.hpc.cam.ac.uk/project/instances/

If you want to access via ssh, you will need to modify the appropriate security group
to allow SSH traffic (i.e. TCP ingress on port 22).
https://cumulus.openstack.hpc.cam.ac.uk/project/security_groups/

To reach your instances over the public internet
(well from anywhere outside the cumulus cloud)
you will need to add attach a floating ip, from the network "internet".
Look at the list of "actions" associated with your server.

For more details please see:
https://docs.openstack.org/horizon/rocky/user/

## Using Application Credientails to access the CLI

If you want to automate the creation of OpenStack resources, the best starting
point is to understand accessing OpenStack via the CLI.

First create your application credentials, selecting all available roles,
via this screen:
https://cumulus.openstack.hpc.cam.ac.uk/identity/application_credentials/

Download either the clouds.yaml or openrc file to your local machine where
you want to run the OpenStack CLI. These credentials will allow you to access
any OpenStack Keystone projected services, with the roles you select, without
having to do an interactive login through a web browser.

Please note that these secrets are very sensitive. If anyone gains access to them,
they will have full access to your account and its data. You can revoke them at
any time via the same web page. 

Now you have the CLI work, take a look at the OpenStack Applicaiton Developer Portal:
https://developer.openstack.org/

## Developing Applications on OpenStack

For advice please see the OpenStack Application Developer Portal:
https://developer.openstack.org/

## What resources are currently available at Cambridge?

There are currently only 8 hypervisors enabled.

TODO...

## Onboarding for 2018/2019

Once invited to access the system, please request an AlaSKA account via:
[https://www.hpc.cam.ac.uk/external-application](https://www.hpc.cam.ac.uk/external-application)

This will setup ssh access to: `alaska-gate.vss.cloud.cam.ac.uk`

### Setting up SOCKS proxy to access Cumulus OpenStack.

At the moment Cumulus OpenStack is isolated in the AlaSKA network.

From your linux desktop/laptop, we create a SOCKS proxy on port 8080 to alaska-gate by running the following command:

```
ssh test123@alaska-gate.vss.cloud.cam.ac.uk -C -D 8080
```

We now configure ssh to use the above proxy when accessing cumulus login node:

```
Host 10.60.150.1
  ProxyCommand=nc -X 5 -x localhost:8080 %h %p
  ForwardAgent yes
```

This allows us to open a ssh session and additional socks proxy to the cumulus login node, using `alaska-gata` by running the following:

```
ssh test123@centos@10.60.150.1 -C -D 8081
```

Now you can configure your browser (or system) to use the socks proxy `localhost:8081`. This forwards the browser requests to the cumulus login node (via alaska-gate).

With the above browser configuration in place, you can access the OpenStack dashboard: `http://10.205.0.1`

Note: the OpenStack dashboard (called Horizon) can be used to download credentails to access OpenStack via the command line.

### Access OpenStack

TODO: add details on how to access the OpenStack deployment.
