tf_aws_elb
===================================

A Terraform module which contains a number of common configurations for AWS ELBs.
* It assumes you're putting your backend instances for the ELBs in a VPC.

Security Group Catalog
----------------------

This module contains the following ELB templates for you to use as modules in
service Terraform templates.

- [elb_external_https](https://github.com/solarce/tf_aws_elb/tree/master/elb_external_https) - This template will create an external facing ELB setup to serve HTTPS traffic.

Usage
------

- See individual module README's for Usage examples.

