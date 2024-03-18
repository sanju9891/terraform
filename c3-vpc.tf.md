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
  create_datebase_subnet_group = true
  create_database_subnet_route_table = true
  database_subnets = ["10.0.151.0/24", "10.0.152.0/24"]

  ##NAT Gateway - outbound Communication
  enable_nat_gateway = true
  enable_nat_gateway = true

  ## VPC DNS Parameters
  enable_dns_hostnames = true
  enable_dns_support = true

  public_subnet-tags = {
    Name = "public-subnets"

  }

  private_subnet_tags = {
    Name = private-subnets"
  }

  databases_subnet_tags = {
    Name = "database-subnets"
  }
  tags = {
    Owner = "kalyan"
    Environment = "dev"
  }
  vpc_tags = {
    Name = "vpc-dev"
  }
}

