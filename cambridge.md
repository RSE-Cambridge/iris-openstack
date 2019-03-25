# IRIS OpenStack @ Cambridge University

The [Cambirdge University](https://www.hpc.cam.ac.uk/) IRIS OpenStack deployment is part of the [Cumulus](https://www.top500.org/system/179577) supercomputer.

For more details please contact John Taylor, StackHPC.

## Authentication

Please vist the OpenStack Horizon Dashboard to login, selecting "Federated Login":
https://cumulus.openstack.hpc.cam.ac.uk/

This will redirect you, via a local Keycloak instances, to EGI AAI (dev instance).
Because we currently only use the dev instance, only grid certificates, google accounts,
and similar are expected to work. Please choose a method that works best for you.

Once IRIS's Indigo IAM setup has access to edugain, the hope is to switch all accounts
to that system. Once complete, you should be able to use your home institution
credentials in a very similar way to the social account.

We are using social credentails to help get early feedback on using this federated
approach.

## Authorization

Once you are able to authenticate with OpenStack, we now need to get you access to some
resources within OpenStack.

While it is hoped Keycloak and/or Indio IAM will eventualy automate the group membership
workflow, this is currently a fairly manual process that can be kickstarted by opening a
bug against this github repository:
https://github.com/RSE-Cambridge/cumulus-config/issues

Please tell us:

* what project you are working on (LSST, Euclid, etc)
* your social email address used to authenticate
* your home instituion email address

This is a manual process. Asking in the #openstack channel in slack may speed things up.

## What resources are currently available at Cambridge?

There are currently only 8 hypervisors enabled.
Given current funding levels we expect to average 40 hypervisors during 2019/2020.

Each hypervisor has two Xeon Gold 6142
(i.e. a total of 64 hyperthreaded cores runing at 2.60 GHz per hypervisor)
with 192GB RAM (i.e. 3GB per hyperthreaded core) and around 400GB of local SSD.
There is a bonded 2 x 25GbE link to a redundant pair of switches.
The hardware includes a 6142F with integrated 100G omni-path, wired into the
cumulus fabric with a 2:1 overcomit, but it is currently unsed by IRIS.

External storage is all provided by a small Ceph cluster. Currently it has
around 45TB of usable space, provided by spinning disks attached to three
servers, each with 4 x 10GbE bond. There are plans to upgrade this capacity
depending on the demand seen.

To get the best performance, please try to:

* boot from a provided base image rather than your own snapshot or uploaded image
* don't boot from a volume, local ssd will take slightly longer to provision, but faster once working
* use the network "cumulus-network" (it is VLAN based, not VXLAN)
* we have very few floating IPs currently available, please use them wisely
* avoid the largest VM size, unless you really need that much memory in one host

## Create your first server

Now you have authenticated, and have been authorized on a project other than the "iris"
holiding project, you can get started using OpenStack and create your first server.

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

## Using CLI with Application Credientails

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
