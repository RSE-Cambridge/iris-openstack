## Welcome to the IRIS Scientific OpenStack Documentation

IRIS aims to create a common eInfrastructure for STFC science.
For more details visit: ttps://www.iris.ac.uk

Below we document the "Scientific OpenStack" digital assets.
Phase 1 is due to be completed at the end of March 2019,
and these documents focus on the deliveriables of this first phase.

We include documentation both for scientists wanting to use IRIS OpenStack sites,
and operators of OpenStack sites wanting to make use of
the current digital assets to create/upgrade/maintain an IRIS OpenStack site.

## Frequently Asked Questions

### What makes an OpenStack site "IRIS compatible"?

We define "IRIS compatible" with a set of tests that determine the capabilities of an OpenStack cloud.
They are designed such that any OpenStack cloud that carries the
("OpenStack Powered Compute")[https://www.openstack.org/brand/interop/] logo
will pass the minimum standards for an IRIS cloud.

As an IRIS user, if you keep the the APIs checked by these tests,
your scirpts or application that access OpenStack will work across all IRIS sites.

There will also be a set of optional features that are tested.
The aim is the reference OpenStack configuration will pass all the tests.

These tests will be able to tell you which of the community maintained
IRIS appliances will be able to work on a given IRIS OpenStack site.

### What IRIS OpenStack sites are currently available?

To request IRIS resources please see:
htps://www.iris.ac.uk/community/requesting-resources-from-iris/

TODO: list the current IRIS sites and their IRIS compatibility test results.

### I have been given OpenStack resources. What should I do next?

Here are links to information on how to access each of the
IRIS funded OpenStack sites:

* RAL[ral]: please contact Alex Dibbo, STFC
* Cambridge[cambridge]: please contant John Taylor, StackHPC

TODO: add docs for each OpenStack site.

### I would like to try out an IRIS Appliance. What should I do next?

One quick way to get started with OpenStack is trying out an IRIS appliance.

Please read the site specific details above first.
Once you have access to OpenStack resources at one of the sites, please try:

* TODO: Get me a Kubernetes Cluster
* TODO: Get me a JuypterHub Cluster
* TODO: Get me a dedicated Slurm Cluster
* TODO: Get me an OpenHPC enabled VM

### I have IRIS hardware I would like to expose uising OpenStack. What should I do next?

We ran a workshop to get some sites started building their site specific
(OpenStack Kayboe)[https://kayobe.readthedocs.io] configuration.
For a digital assest containing the material used at the workshop,
please see:
https://drive.google.com/drive/u/1/folders/1n3yq5AamXx4YIcTfLhIj5Fm9CAjeVOu2
(TODO: add static tarball)

Phase 1 is using the Cambridge University OpenStack deployment as a reference.
Firstly here is the reference archtecture documentation:
https://drive.google.com/drive/u/1/folders/1bIMrAPNfbGWO0ptWd7MEGF3vHUIpsDVM
(TODO: add static tarball)
