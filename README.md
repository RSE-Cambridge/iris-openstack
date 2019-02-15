## Welcome to the IRIS Scientific OpenStack Documentation

![IRIS logo](https://www.iris.ac.uk/wp-content/uploads/2018/07/iris-circle-100x100.png)

IRIS aims to create a common eInfrastructure for STFC science.
For more details visit:
[https://www.iris.ac.uk](https://www.iris.ac.uk)

Below we document the "Scientific OpenStack" digital assets.
Phase 1 is due to be completed at the end of March 2019,
and these documents focus on the deliveriables of this first phase.

We include documentation both for scientists wanting to use IRIS OpenStack sites,
and operators of OpenStack sites wanting to make use of
the current digital assets to create/upgrade/maintain an IRIS OpenStack site.

## Frequently Asked Questions

The documention is structured as FAQs below.

### What makes an OpenStack site "IRIS compatible"?

To run the conformance tests please see: [IRIS Conformance Tests](iris-conformance-tests)

We define "IRIS compatible" with a set of tests that determine the capabilities of an OpenStack cloud.
They are designed such that any OpenStack cloud that carries the
[OpenStack Powered Compute](https://www.openstack.org/brand/interop/)
certification will pass the minimum standards for an IRIS cloud.
These tests can be run against any OpenStack cloud, not just IRIS OpenStack clouds.

If you use only the APIs checked by these tests,
your scirpts/application should work across all IRIS sites.

There will also be a set of optional features that are tested.
The aim is the digital assets containing the reference OpenStack
configuration will help sites run OpenStack deployments that can
pass all of the IRIS compatible tests.

Packaged IRIS Appliances should document if they need any of the optional tests.
This should help you work out what appliances will work at what sites.

### How can I get access to IRIS OpenStack resources?

To request IRIS resources:
[https://www.iris.ac.uk/community/requesting-resources-from-iris/](https://www.iris.ac.uk/community/requesting-resources-from-iris/)

To start a free trail with an OpenStack public cloud: [https://www.openstack.org/passport](https://www.openstack.org/passport) 

### I have been given OpenStack resources. What next?

Here are links to information on how to access each of the
IRIS funded OpenStack sites:

* [RAL](ral)
* [Cambridge](cambridge)

### What applications are available on IRIS OpenStack?

One quick way to get started with OpenStack is trying out an IRIS appliance.

Once you have access to OpenStack resources, please try:

* [Get a Computer with OpenHPC and Conda](computer)
* [Kubernetes Cluster](k8s)
* [Juypter notebooks via JupterHub](juypter)
* [Dedicated Slurm cluster](slurm)

TODO: add docs so above links are not broken.

### I have IRIS hardware I would like to expose uising OpenStack. What should I do next?

We ran a workshop to get some sites started building their site specific
[OpenStack Kayboe](https://kayobe.readthedocs.io) configuration.
For a digital assest containing the material used at the workshop,
please see:
[https://drive.google.com/drive/u/1/folders/1n3yq5AamXx4YIcTfLhIj5Fm9CAjeVOu2]
https://drive.google.com/drive/u/1/folders/1n3yq5AamXx4YIcTfLhIj5Fm9CAjeVOu2
(TODO: add static tarball)

Phase 1 is using the Cambridge University OpenStack deployment as a reference.
Firstly here is the reference archtecture documentation:
[https://drive.google.com/drive/u/1/folders/1bIMrAPNfbGWO0ptWd7MEGF3vHUIpsDVM](https://drive.google.com/drive/u/1/folders/1bIMrAPNfbGWO0ptWd7MEGF3vHUIpsDVM)
(TODO: add static tarball)
