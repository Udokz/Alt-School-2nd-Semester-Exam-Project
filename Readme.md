# Provisioning a Linux Ubuntu Server with a Simple HTML Page

## Project Overview
This project demonstrates the provisioning of an Ubuntu Linux server on AWS to host a static HTML webpage. It includes the manual installation of Apache2, deployment of a simple HTML file, and further instructions for testing the setup.

## Features
- Provisioning an Ubuntu server on AWS (Amazon Web Service).
- Installation of and configuration of Apache2 as the web server.
- Deployment of a static HTML page

## Requirements
- An AWS account.
- AWS CLI installed and configured, or any other CLI tool compatible with AWS.
- SSH client installed on your local machine.
- Basic knowledge of Linux and web servers.


## Let's Get Started
### 1. Launch an Ubuntu instance on AWS
1. Log in to your AWS Management Console.
2. Launch a new EC2 instance with the following details:
- **AMI:** Ubuntu 22.04 or later
- **Instance Type:** t3.micro (or any preferred type)
- **Security Group:** Allow inbound traffic on port 22 (SSH), port 80 (HTTP), and port 443 (HTTPS), and allow all outbound traffic.
- Create or use an existing key-pair (key.pem file) for SSH
3. Download the key-pair file and make it readable and secure by running:
```bash
sudo chmod 400 <your-key.pem>
```
4. Note the public IP address or DNS of your instance.


### 2. Connect to the Instance
Use SSH to connect to your instance:
```bash
ssh -i <your-key.pem> ubuntu@<your-instance-ip>
```

### 3. Install Apache2
Once connected to the server, install Apache2:
```bash
sudo apt update
sudo apt upgrade
sudo apt install apache2 -y
```

### 4. Write and Deploy the HTML File
#### Create the HTML File Locally
    1. Use a code editor like Visual Studio Code to create your HTML file locally:
   - Open Visual Studio Code and create a new file named `index.html`.
   - Add the following content to the file:
  ```html
     <!DOCTYPE html>
     <html>
     <head>
         <title>Linux Project 1</title>
     </head>
     <body>
         <h1>Hello, Linux!</h1>
         <p>Welcome to Apache2 web server</p>
     </body>
     </html>
   ```
   - Save the file.


   #### Upload to a Git Repository
   1. Initialize a new Git repository:
```bash
   git init
   ```

   2. Add the `index.html` file and commit it:
```bash
   git add index.html
   git commit -m "Initial Commit for Linux Project"
   ```

   3. Push the repository to your GitHub.
   - For GitHub:
```bash
     git remote add origin https://github.com/<your-username>/<your-repository>.git
     git push -u origin main
```

     #### Get the Link to the ZIP File
    1. On your Github, navigate to your repository.
    2. Click on the "Code" button and select "Download ZIP".
    3. Copy the link to the ZIP file by right-clicking on "Download ZIP" and selecting "Copy Link Address".


#### Deploy the HTML File to the Server
    1. On your AWS instance, navigate to the `/var/www/html` directory:
```bash
   cd /var/www/html
   ```

   2. Use `wget` to download the ZIP file from your Git repository (replace `<zip-url>` with the ZIP file URL):
```bash
   sudo wget <zip-url>
   ```

   3. Install the `unzip` utility if not already available:
```bash
   sudo apt install unzip -y
   ```
   
   4. Unzip the file:
 ```bash
   sudo unzip <zip-file-name>.zip
   ```

   5. Copy the `index.html` file from the extracted folder to the `/var/www/html` directory (adjust the path if necessary):
```bash
   sudo cp <extracted-folder>/*.html /var/www/html/
   ```

   6. Verify the file is in place:
```bash
   ls
   ```


## Result (Screenshot Of Live HTPP Page)
![Screenshot of HTTP Live Page](./Assets/Screenshot%20of%20the%20live%20HTPP%20page.png)
Fig 1. Screenshot of the HTTP live page





### IP Address
- 16.171.7.208



## Contributing
Contributions are welcome! Feel free to fork the repository and submit a pull request.

## Acknowledgments
- [AWS](https://aws.amazon.com/)
- [Ubuntu](https://ubuntu.com/)
- [Apache2](https://httpd.apache.org/)
- [Let's Encrypt](https://letsencrypt.org/)






















   












