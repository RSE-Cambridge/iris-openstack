# IRIS OpenStack @ Cambridge University

The [Cambirdge University](https://www.hpc.cam.ac.uk/) IRIS OpenStack deployment is part of the [Cumulus](https://www.top500.org/system/179577) supercomputer.

For more details please contact John Taylor, StackHPC.

## Onboarding for 2019/2020

Soon we hope to enable external access to OpenStack APIs, with a federated login.

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
