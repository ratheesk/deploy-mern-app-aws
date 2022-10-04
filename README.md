# Mern Deployment in AWS!
how to deploy a MERN environment that is composed of Ubuntu 22.04 servers providing users access to the application through an Nginx reverse proxy to the application server in aws ec2.

## Instance creation in aws

1. Log in to the AWS console
2. Go to **instances**
3. Click **Launch Instances**
4. Add your **instance name**
5. Select **ubuntu** server
6. Select instance type **t2.micro**
7. In network settings add following security group rules

| Type      |Port range              |Source type|Source            |
| ----------| ---------------------- | --------- |----------------- |
| SSH       | 22                     |Anywhere   |0.0.0.0/0         |
| HTTP      | 80                     |Anywhere   |0.0.0.0/0 and ::0 |
| HTTPS     | 443                    |Anywhere   |0.0.0.0/0         |
| Custom TCP| 5000 (Node server port)|Anywhere   |0.0.0.0/0         |

8. Create new keypair with .pem and save it on your computer
9. **Launch** your instance

## Log in to your server

1. Go to the .pem file location and open terminal
2. Replace your Public IPv4 DNS

    ``` ssh -i visAct.pem ubuntu@Public_IPv4_DNS ```