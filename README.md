# Red-Route53-Interactive
Manage RedTeam DNS over Ansible

## Requirements

To use this ansible role you'll need to have ansible installed (kinda obvious there)
Furthermore you'll need to have python3 and boto installed
```
pip3 install boto boto3

```
You will also need to have an AWS IAM user that has the capabilities of full control over Route53.
for more info on how to do that, please read the documentation over at AWS: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html#id_users_create_console

This role does **NOT** automatically generate DNS zones for you. 
Please register the domains (and create their respective zones) you'd like to use in Route53 manually.

## Usage
This role is intented to be used in combination with my Red-EC2 role (https://github.com/jfmaes/Red-EC2). 
<br>However, it can be used sepperatly as well (as all good Ansible roles should be). In which case this role will need an inventory file, or be preceeded by another role that creates a dynamic inventory. In this case you'll need to override the default xx_host_identifier variables in this role. 

## Role variables

### AWS specific variables
| variable  	| default value  	|  description 	|   	
|:-:	|:-:	|:-:	|	
|   aws_access_key	| N/A   	|  needed to auth to AWS  	|   	   	
| aws_secret_key  	| N/A  	| needed to auth to AWS  	|   

### Route 53 specific variables

| variable  	| default value  	|  description 	|   	
|:-:	|:-:	|:-:	|	
|   C2_host_identifier	| C2  	|  the group variable used for C2 instances in Ansible's (dynamic) inventory 	|   	   	
| redir_host_identifier  	| Redirector 	| the group variable used for Redirector instances in Ansible's (dynamic) inventory  	|   
| redelk_host_identifier  	| RedELK  	| the group variable used for RedELK instances in Ansible's (dynamic) inventory  	| 
|overwrite| no | if DNS should be overriden in case the record already exists.  |
