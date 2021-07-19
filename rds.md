Create the rds resource
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/db_instance

https://learn.hashicorp.com/terraform



application---pom.xml-----database(user-petlinic)

Goto the same folder of eks 

resource "aws_db_instance" "mysql" {
  allocated_storage    = 10
  engine               = "mysql"
  engine_version       = "5.7"
  instance_class       = "db.t3.micro"
  name                 = "mydb"
  username             = "learndevops"
  password             = "Kmbvvttei91ccvambsCs"
  parameter_group_name = "default.mysql5.7"
  skip_final_snapshot  = true
  db_subnet_group_name   = aws_db_subnet_group.education.name
}


create the subnet group
group the private subnet
call that subnet group to the RDS


resource "aws_db_subnet_group" "education" {
  name       = "education"
  subnet_ids = module.vpc.private_subnets

  tags = {
    Name = "Education"
  }
}


resource "aws_security_group" "rds" {
  name   = "education_rds"
  vpc_id = module.vpc.vpc_id

  ingress {
    from_port   = 3306
    to_port     = 3306
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  egress {
    from_port   = 5432
    to_port     = 5432
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  tags = {
    Name = "education_rds"
  }
}


======================================
resource "aws_db_subnet_group" "education1" {
  name       = "education1"
  subnet_ids = module.vpc.private_subnets

  tags = {
    Name = "Education"
  }
}

resource "aws_db_instance" "mysql" {
  allocated_storage    = 10
  engine               = "mysql"
  engine_version       = "5.7"
  instance_class       = "db.t3.micro"
  name                 = "mydb"
  username             = "learndevops"
  password             = "Kmbvvttei91ccvambsCs"
  parameter_group_name = "default.mysql5.7"
  skip_final_snapshot  = true
  db_subnet_group_name   = aws_db_subnet_group.education1.name
}
