### Create VPC
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "5.6.0"
  name = "my-vpc"
  cidr = "10.0.0.0/16"

 azs             = ["ap-south-1a", "ap-south-1b"]
  private_subnets = ["10.0.1.0/24", "10.0.2.0/24"]
  public_subnets  = ["10.0.101.0/24", "10.0.102.0/24"]

  ### Database subnets
  database_subnets = ["10.0.151.0/24", "10.0.152.0/24"]

}

