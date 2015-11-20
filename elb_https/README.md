elb_https
==================
A Terraform module for creating an ELB with HTTPS

It makes the following assumptions in its design:
* You have subnets in a VPC and that you want the ELB in two subnets,
  in the first two AZs of the region.
* You'll build all your instances with an Auto-Scaling Group (ASG)
  and you'll use the ASG to associate your instances with the ELB.
* Your instances behind the ELB will be in a VPC
* It only configures a listener for HTTPS
* It requires you've already uploaded an SSL certificate to EC2
* Cross Zone Load Balancing is enabled
* Connection Draining is enabled

It supports both (one or the other):
- Internal IP ELBs
- External IP ELBs

It's recommended you use this with
[sg_https_only](https://github.com/terraform-community-modules/tf_aws_sg/tree/master/sg_https_only#sg_https_only-terraform-module)

Input Variables
---------------

- `elb_name` - The friendly name of the ELB
- `elb_security_group` - The Security Group to associate with the ELB
- `elb_is_internal` - Defaults to `false`, you can set to `true` to make
   the ELB have an internal IP
- `idle_timeout` - (Optional) 
- `connection_draining_timeout` - (Optional)
- `ssl_certificate_id` - The ARN of the SSL certificate
- `subnet_az1` - The VPC subnet ID for AZ1
- `subnet_az2` - The VPC subnet ID for AZ2
- `backend_port` - The port the service running on the EC2 insances
    will listen on.
- `backend_protocol` - The protocol the service on the backend_port
    understands, e.g. `http` 
    - The possible options are:
    - http
    - https
    - tcp
    - ssl (secure tcp)
- `health_check_target` - The URL that the ELB should use for health
    checks, e.g. `HTTPS:443/health`
- `idle_timeout` - The time in seconds that the connection is allowed to be
    idle. (default: 60)
- `connection_draining_timeout` - The time in seconds to allow for connections
    to drain. (default: 300)

Outputs
------

- `elb_id`
- `elb_name`
- `elb_dns_name`

Usage
-----

You can use these in your terraform template with the following steps.

1.) Adding a module resource to your template, e.g. `main.tf`

```
module "my_web_elb" {
  source = "github.com/terraform-community-modules/tf_aws_elb/elb_https"
  elb_name = "${var.elb_name}"
  subnet_az1 = "${var.subnet_az1}"
  subnet_az2 = "${var.subnet_az2}"
  backend_port = "${var.backend_port}"
  backend_protocol = "${var.backend_protocol}"
  ssl_certificate_id = "${var.ssl_certificate_id}"
  health_check_target = "${var.health_check_target}"
  aws_access_key = "${var.aws_access_key}"
  aws_secret_key = "${var.aws_secret_key}"
  aws_region = "${var.aws_region}"
}
```

2.) Setting values for the following variables, either through `terraform.tfvars` or `-var` arguments on the CLI

- aws_access_key
- aws_secret_key
- aws_region
- elb_name
- subnet_az1
- subnet_az2
- backend_port
- backend_protocol
- ssl_certificate_id
- health_check_target
- idle_timeout
- connection_draining_timeout
