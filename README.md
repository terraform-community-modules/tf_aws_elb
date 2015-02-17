tf_aws_elb
===================================

A Terraform module which contains a number of common configurations for AWS ELBs.
* It assumes you're putting your backend instances for the ELBs in a VPC.

ELB Catalog
-----------

This module contains the following ELB templates for you to use as modules in
service Terraform templates.

- [elb_https](https://github.com/solarce/tf_aws_elb/tree/master/elb_https) - This template will create an ELB setup to serve HTTPS traffic.
    - Defaults to external but can be made internal by setting the `elb_in_internal` variable to `true`
    - We recommend you use this with the [sg_https_only](https://github.com/solarce/tf_aws_sg/tree/master/sg_https_only#sg_https_only-terraform-module) security group module

Usage
------

- See individual module README's for Usage examples.

