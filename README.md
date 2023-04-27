# Terraform
(Infrastructure as Code (Iac) by using Terraform on AWS.)
Installation step: 
-install terraform on ubuntu.
-creating an access key or security credentials on aws.
-creating terraform file terraform.tf 

provider "aws" {
  region     = "ap-southeast-1"
  access_key = "xxxxxxxxx"
  secret_key = "xxxxxxxxxxxxxxxxxxxxxx"
}
resource "aws_instance" "ec2-example" {
  ami           = "ami-02045ebddb047018b"
  instance_type = "t2.micro"
  user_data     = "${file("install_apache.sh")}"
}

-creating a bash script ("install_apache.sh") for install an apache2 server.
#! /bin/bash
sudo apt-get update
sudo apt-get install -y apache2
sudo systemctl start apache2
sudo systemctl enable apache2

-initialize terraform applying commend $terraform init
-verify/check the infrastructure applying commend $terraform plan
-apply to create infrastructure as a code applying commend $terraform apply
-then login to aws console to verify the infrastructure and application is running properly.
