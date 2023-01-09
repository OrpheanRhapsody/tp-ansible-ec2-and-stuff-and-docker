# Ansible training

README being written.

## Usage

`ansible-playbook -i inventories/inventory.ini main.yaml`

## Steps explained

I've set up my AWS environment by using the AWS CLI `aws configure` and the environment variables `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`.  
  
  
  
The goal of the project was to create (at least) one EC2 instance with several requirements (VPC, Internet Gateway, Security group which allows SSH connection, creation of a SSH Key pair).

- The project is organized as follow:
```
├── README.md                           --> this file
├── ec2.yaml                            --> playbook which calls all the necessary roles til the EC2 creation.
├── docker.yaml                         --> playbook which calls the docker role
├── group_vars
│   └── all                             --> directory containing some variables used through the pipeline
├── inventories
│   └── inventory.ini                   --> main inventory file
├── main.yml                            --> main playbook which calls the ec2 and docker playbooks
└── roles                               
    ├── aws-add-ec2-to-inventory        --> role to add the EC2 instance created to the inventory (to further refer to it)
    ├── aws-ec2                         --> role to create the EC2 instance
    ├── aws-igw                         --> role to create the subnet associated to the VPC created, the internet gateway and to route the igw 
    ├── aws-keypair                     --> role to create and save the ssh key pair.
    ├── aws-secgroup                    --> role to create the security group 
    ├── aws-vpc                         --> role to create the vcp
    └── docker-ubuntu                   --> role to install Docker on a Ubuntu instance
```

As for now, Docker only install an hello world image.