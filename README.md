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

## Install Nodejs

1. Run system update

   ```sudo apt-get update```

2. install curl

   ```sudo apt install curl -y```

3. Check available Node.js Version

   ```sudo apt policy nodejs```

4. Add Nodejs latest repo on Ec2 Ubuntu

   ```curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - ```

5. Install Nodejs & NPM

   ```sudo apt-get install nodejs```

6. Check the installed version of node

   ```node -v```

7. Check the installed version of npm

   ```npm -v```

## Install Nginx

1. Install nginx

   ```sudo apt-get install nginx```

2. Start nginx

   ```sudo service nginx start```

3. Check nginx status

   ```sudo service nginx status```

4. Exit nginx status

   ```q```

## Install nano text editor

1. Run system update

   ```sudo apt-get update```

2. Install the editor

   ```sudo apt-get install nano```

## Install pm2

1. Run system update

   ```sudo apt-get update```

2. install pm2

   ```sudo npm install pm2 -g```

3. Configure PM2 to start Express application at startup.

   ```sudo env PATH=$PATH:/usr/local/bin pm2 startup -u ubuntu```

## Clone MERN app

1. Run system update

   ```sudo apt-get update```

2. Clone from git hub

   ```git clone <url>```

3. Input your github account name

4. Input your password

## Build the react app

1. Navigate to client folder

   ```cd client_folder_path```
2. Install depencies

   ```sudo npm install```

3. Build the app

   ```sudo npm run build```

## Run the node server

1. Navigate to server folder

   ```cd server_folder_path```

2. Install depencies

   ```sudo npm install```
3. Create .env file ,add credentials and save it

   ```sudo nano .env```

4. Run the app with pm2

   ```pm2 start app.js```

5. Freeze a process list on reboot

   ```pm2 save```

6. Display all processes logs in streaming

   ```pm2 logs```