## Terraform Block
terraform {
  required_version = "~> 0.14"
  required_providers {
    aws = {
      source = "hashicoop/aws"
      version = "~> 3.0"
    }
  }
}

### Provider Block
provider "aws" {
  region = var.aws_region
  profile = "default"
}