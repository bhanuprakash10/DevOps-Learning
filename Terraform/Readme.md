Terraform is an infrastructure as a code (IaC) tool that allows you to build, change and version infrastructure safely and efficiently.
Developed by Hashicorp.
Terraform users define and enforce infrastructure configurations by using a JSON-like configuration language called HCL (HashiCorp Configuration Language).

## Components of Terraform:
- Providers
- Resources
- Variables
- Statefile
- Provisioners
- Backends
- Modules
- Data Sources
- Service Principals

### Providers:
- Terraform relies on plugin called "Providers" to interact with cloud providers, SaaS providers, and other APIs.
- Every resource type is implemented by a provider; without providers, Terraform can't manage any kind of infrastructure.

Example:
```
provider "aws" {
  region = "us-east-1"
}
```
### Resources:
- Resources are the most important element in the Terraform language. Each resource block describes one or more infrastructure objects, such as virtual networks, compute instances, or higher-level components such as DNS records.

Example:
```
resource "aws_instance" "web" {
  ami           = "ami-a1b2c3d4"
  instance_type = "t2.micro"
}
```
### Variables:
- Using variables in terraform configurations make our deployment dynamic
- A separate file with name "variable.tf" needs to be created in the working directory to store all variables for our used in main.tf configuration file.

Example:
```
variable "image_id" {
  type = string
}

variable "availability_zone_names" {
  type    = list(string)
  default = ["us-west-1a"]
}
```
### Statefile:
- After the deployment is finished terraform creates a state file to keep a track of current state of the infrastructure.
- It will use this file to compare when you deploy/destroy resources, in other words it compares "current state" with "desired state" using this file.
- A file with name of "terraform.tfstate" will be created in your working directory

    Restoring Statefile:
        - If the statefile is deleted or corrupted, we can restore it using terraform import command
        Example: ```terraform import <terraform resource name> <resource id> ```
### Provisioners:
- Provisioners provide the ability to run additional steps or task when a resource is created or destroyed.
- This is not a replacement for configuration management tool.

Types of Provisoners:
- File
- Local-Exec
- Remote-Exec

Example:
```
provisioner "file" {
  source      = "conf/myapp.conf"
  destination = "/etc/myapp.conf"

  connection {
    type     = "ssh"
    user     = "root"
    password = "${var.root_password}"
    host     = "${var.host}"
  }
}
```
### Modules:
- A module defines a set of parameters which will be passed as key value pair to actual deployment.
- With this approach you can create a multiple envoironment in a very easy way.
- If you want to perform a template-based deployment you can follow modularized approach

Example:
```
module "module_dev"{
    source = "./modules"
    prefix = "dev"
}    
```
### Data Sources:
- If you deploy your resources out of terraform and use them in your terraform code the way you ue them through "Data Source"
- Data Source in terraform are used to get information anout external resources to terraform, and use them to set up your terraform resources.

Example:
```
data "aws_s3_bucket" "example" {
  bucket = "example-bucket"
}

output "bucket_name" {
  value = data.aws_s3_bucket.example.bucket
}
```
### Local Variables:
- A local value assigns a name to an expression, so you can use the name multiple times within a module instead of repeating the expression.
- Local values can be helpful to avoid repeating the same values or expressions multiple times in a configuration
Note: Local values are created by a locals block (plural), but you reference them as attributes on an object named local (singular). Make sure to leave off the "s" when referencing a local value!

Examples: 
```
locals {
  instance_ids = concat(aws_instance.blue.*.id, aws_instance.green.*.id)
}

locals {
  common_tags = {
    Service = local.service_name
    Owner   = local.owner
  }
}
```
