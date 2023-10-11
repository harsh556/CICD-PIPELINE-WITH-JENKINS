# CICD-PIPELINE

**I was given a task to create a CICD Pipeline for a Random Github repo. Here is how I approached to This Assignment**


**A. Create an AWS EC2 Instance (server) on which Jenkins will be deployed**

1 . Go to AWS Free tier and sign in to your free tier account (If don't have one your can Create one by cliking on Create New Account).


![Screenshot 2023-10-11 084346](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/010ca701-7373-48d9-bedd-a4a37b1b15d3)


 - Your AWS Console will look like this :-


   ![AWS console](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/eba27b16-c4d2-48ac-baa7-f5afaf6e8c5c)


2 . In the search Panel,Type Ec2 to search for the Ec2 Service


   ![Searching EC2](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/efc0c2e3-642c-4115-bbd4-f9b4759edb71)


3 . Click on Ec2 to go the Ec2 Console


  ![Ec2 Console](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/558ab04e-c2a2-4206-8ea4-608a259d5954)


4 . click on Launch Instances.

5 . Enter your Instance Name.


   ![Name_of_EC2](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/b7e67db5-a799-4472-b743-9747eaffc3a8)


6 . Give AMI(template for the OS) for your Server .


   ![AMI](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/0b807250-fa73-4110-b259-91e3357e8f7b)


7 . Specify the instance Type(Required for the CPU and Storage you will use)
   

![Instance Type](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/38830082-42c9-4b2a-ac5c-aab3d4f74da1)


8 . Create a New keypair which is basically required to ssh into the server remotely . (AES)
  

![Keypair](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/bd2b31b6-8499-401d-b54e-09c48065bc6f)


 -  Name your key file and let the rest configuration as they are


![Create_keypair](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/26055cc1-aeb5-4c31-bc3a-ea08dfd9306d)


9 . Configure the storage Capacity and Launch the Instance


![Storage+launch](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/f43e4a71-bcbc-47b5-9349-51ca7a0878b6)


**You have your server running**

10 . Select Your Server and Click on Connect


![Click On Connect](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/c173d9f1-778e-4e28-baa2-2f6243435593)


11 . There are various options for connecting to the server, But we will Click on EC2 Instance Connect . It Opens the server terminal in the Browser itself .


![Click_Instance_Connect](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/7c3d45d9-3e66-41c8-a3c5-4c721b36d36f)


12 . Server shell appears 


![ssh](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/c93db808-a148-4d1a-afab-8de2cc1d722d)


**B. Installation of Jenkins**

1. For Jenkins to run successfully, We must Install Java Development kit first.

    Commands To Run :-

     - sudo apt update
     - sudo apt install fontconfig openjdk-17-jre

    To Verify the Installation, Run Command - java -version

2. Now We Will Install Jenkins For Our Ubuntu server

   Commands To Run :-

     - curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \ /usr/share/keyrings/jenkins-keyring.asc > /dev/null
     - echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \ https://pkg.jenkins.io/debian-stable binary/ | sudo tee \ /etc/apt/sources.list.d/jenkins.list > /dev/null
     - sudo apt-get update
     - sudo apt-get install jenkins

**C. Let's go to the Jenkins Server**

1. Open a new tab and Copy the Public IP of the Server with Port 8080 (default Port of Jenkins) .


![Jenkins_1page](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/d3c98016-23e8-4234-a3e1-54b537e8e2b2)


2. Go to Your Server and Run Command - sudo cat /var/lib/jemkins/secrets/initialAdminPassword

   This Will give you your Admin Password to proceed further.

3. Create your Account

   ![Create_First_Admin_User](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/8da80d54-1266-4f9c-aea8-593d1c2dcb26)
   

4. Install suggested Plugins



![Install_suggested_plugins](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/cbd7e6b8-edb1-487e-a960-112216b4b638)



 - Getting started


![getting started](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/f00581ac-ccc2-4e53-99b3-83e0bda67a40)


- Jenkins Url

  
   ![Jenkins url](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/0bdb562c-7f24-4970-b483-d90d1f3e8946)


5. Sign up to your Acount That you Created

   - The Main Console Appears

    
![Jenkins Main Console](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/ed3ddad0-088e-4638-832e-6d84c75928a1)


6. For Running the Project That was given As a task to be Deployed in a CICD Pipeline, We Need the Following Plugins.


   - GitHub
  
   - Pipeline
  
   - NodeJS
  
   - Also We Need to install nodejs on or server too so that the Pipeline Runs smoothly as at the first place all the Command will run on our Server itself as we haven't used Multiple agents for multiple 
     stages.

      Command - sudo apt install npm (This will install both npm as well as NodeJS as with apt it downloads all the required dependencies)

7. For the Plugins to get Installed :-

   - Go to Manage jenkins From The Left Panel and Click on Plugins in the Next Window.


     ![Manage_Plugins](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/63578e01-6655-4744-ae81-99cf375e698b)


  - Check For the Following Plugins in Installed Plugin and If They are not the Click on Available Plugins and Install the necessary Plugins :-

     - [ ] Github
     - [ ] Pipeline
     - [ ] NodeJS

8. For The Creation of the Pipeline

 - Click on New item in the main Dashboard

 - Select Pipeline and give your pipeline any name of your Choice


   ![Item](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/03321493-8b69-41d5-8cac-22da579fdd46)


- leave All the Configuration as they are and go down to the Scripts


  ![script](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/8cb2316e-9953-4039-95c4-3682b1c54968)


- Paste the Following Script Over there :-


   pipeline {
    agent any
    
    environment {
        // Define environment variables if needed
        NODE_VERSION = '14'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    sh 'git clone https://github.com/harsh556/react-ssr'
                    sh 'cp ./react-ssr/* ./ -r'
                    sh 'rm -rf ./react-ssr'
                }
            }
        }


        stage('Build') {
            steps {
                script {
                    // Install Node.js and dependencies
                    def nodeHome = tool 'NodeJS'
                    env.PATH = "${nodeHome}/bin:${env.PATH}"
                    sh 'npm cache clean --force'
                    sh 'npm install'
                    
                    // Build the React application
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'npm run dev'
                    sh 'echo "Deploying to Azure/DigitalOcean/Heroku/AWS/GCP..."'
                    // Add deployment steps here
                }
            }
         }
     }
 }


 - Click on save or apply.

   **Our Pipeline is ready, Click On Build Now**

   **But here Our  Pipeline failed because of syntax error that was there in the github repo that we were using for this Demo**

   **Errors :-**
 
      
    ![Error With The Code](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/703be13b-6a02-4b53-b57e-0852d393a271)



   
   ![Error With the code 2](https://github.com/harsh556/CICD-PIPELINE/assets/114024228/95ae0eed-574c-4537-8aec-e9dfb129a826)



   

   
   
