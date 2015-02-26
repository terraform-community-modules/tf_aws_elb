tf_aws_elb
===================================

A Terraform module which contains a number of common configurations for AWS ELBs.
* It assumes you're putting your backend instances for the ELBs in a VPC.

ELB Catalog
-----------

This module contains the following ELB templates for you to use as modules in
service Terraform templates.

- [elb_https](https://github.com/terraform-community-modules/tf_aws_elb/tree/master/elb_https) - This template will create an ELB setup to serve HTTPS traffic.
    - Defaults to external but can be made internal by setting the `elb_in_internal` variable to `true`
    - We recommend you use this with the [sg_https_only](https://github.com/terraform-community-modules/tf_aws_sg/tree/master/sg_https_only) security group module
- [elb_http](https://github.com/terraform-community-modules/tf_aws_elb/tree/master/elb_http) - This template will create an ELB setup to serve HTTP (TCP 80) traffic.
    - Defaults to external but can be made internal by setting the `elb_in_internal` variable to `true`

Usage
------

- See individual module README's for Usage examples.

Authors
=======

Created and maintained by [Brandon Burton](https://github.com/solarce)
(brandon@inatree.org).

License
=======

Apache 2 Licensed. See LICENSE for full details.
