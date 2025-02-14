# Jenkins
Jenkins is an open-source solution comprising an automation server to enable continuous integration and continuous delivery (CI/CD), automating the various stages of software development such as build, test, and deployment. 

Jenkins is a Java-based open-source automation platform with plugins designed for continuous integration. It is used to continually create and test software projects, making it easier for developers and DevOps engineers to integrate changes to the project and for consumers to get a new build. 
# What Is Jenkins Used For?
Jenkins software’s popularity stems from its ability to track and monitor repetitive activities that emerge throughout a project’s development. For example, if your team is working on a project, Jenkins will continually test your builds and alert you to any mistakes early in the process
#  Jenkins is the  heart of software development life cycle
- jenkin is an open source,project written in JAVA that run windows ,MacOS,and other unix-like Operating system
- It helps automate the parts of software development related to building, testing, and deploying, facilitating DevOps practices.
- it is free
- strong community support
- lost off plugins are available
- worked on port no.8080
- jenkins automate the entire  SDLC
- jenkins was originally developed by sun microsystem in 2004 under the hudson=jenkins/hudson(paid)
- whenever developers write code ,we integrate all that code of all developers at that point of time and we build ,test and delever/deploy to the client . This process is called CI/CD.
- because of CI nows bugs will be reported fast and get rectified foot so the entire software development happen fast.

<h2> Developers---➡️ Github ---➡️JENKINS ---➡️Build tool(Maven)----➡️Test tool (Selenium)
</h2
     
  # Plugins = plug and play (those tools communicate each other)
  # artifact = Archive(store those code ready for final deployment)
  - 1)Once developer puts code in github ,jenkins pull that code and send to maven fr build
  - 2)Once build is done ,jenkins pull that code and send to Selenium for testing.
  - 3)Once testing is done ,then jenkins will pull that code and send to artifactory(archiving purpose) as per requirement and so on.
  
  # advantages
  - it has lots of plugins available
  - you can write your own plugins
  - you can use community plugins
  - Jenkins is not just tool it is a framework i.e you can do whatever you want all you need is plugins
  - we can attach slaves (nodes)to jenkins master .it instruct other slaves to do jobs (work distribute to slaves)

  # BUILD
  compile---➡️Code review---➡️unit testing--➡️integration testing--➡️packaging(WAR,JAR)
  -
  - Anything you can create in jenkins or via jenkins are saved in this directory= <h2> /var/lib/jenkins/workspace </h2>

# Installation of JENKINS
- firstly you have to create an instance of ubuntu or any of them.
- after that connect the instance to SSH terminal
- In terminal you have insatll java in you VM (jenkins require java to run. /becoz,jenkins built in JAVA)
- **sudo apt update**
- **sudo apt install fontconfig openjdk-17-jre (open java development kit)**
- **java -version**
openjdk version "17.0.8" 2023-07-18
OpenJDK Runtime Environment (build 17.0.8+7-Debian-1deb12u1)
OpenJDK 64-Bit Server VM (build 17.0.8+7-Debian-1deb12u1, mixed mode, sharing)
- On Debian and Debian-based distributions like Ubuntu you can install Jenkins through apt.
- **Long Term Support release**
A LTS (Long-Term Support) release is chosen every 12 weeks from the stream of regular releases as the stable release for that time period. It can be installed from the debian-stable apt repository.
- **sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key**
- Save the GPG Key to the Keyrings Directory: The **/usr/share/keyrings** directory is a common place to store keyrings on Debian-based systems. By saving the GPG key to this directory, you ensure that it’s available for use by the package manager to verify the packages from the Jenkins repository.
**Why This Step is Necessary**
- When you install Jenkins on a Debian-based system (such as Ubuntu), you typically add the Jenkins package repository to your list of sources. The package manager (APT) needs to verify the integrity and authenticity of the packages it downloads from this repository. This verification is done using the GPG key.
- Without this GPG key, your system would not be able to verify that the packages from the Jenkins repository are legitimate. This could pose a security risk, as you might inadvertently install compromised or tampered packages.
- **echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null**
- The command you provided is used to add the Jenkins repository to your system's list of package sources on a Debian-based system, such as Ubuntu. This allows you to install Jenkins using the package manager (APT) and ensures that you receive updates directly from the Jenkins repository.
- This adds the Jenkins repository to your system's list of APT sources.
- It specifies the URL for the Jenkins repository (https://pkg.jenkins.io/debian-stable) and the distribution/component (binary/).
- It uses the keyring file (jenkins-keyring.asc) to verify the integrity of the packages.
- After adding the repository ,you update your package list
- **sudo apt update**
- Install Jenkins:
Finally, you install Jenkins using:
- **sudo apt insatll jenkins**
- you can check the service status of your jenkins tool using cmd
- **systemctl status jenkins**
- **ps -ef | grep jenkins**
- Access jenkins to web hit your public IP to web browser with port 8080(https://ip:8080)
- this directory can shown your admin password required for login jenkins  **/var/lib/jenkins/secrets/intialAdminPassword**
- setup jenkins
- start using jenkins.

<h3>Tutorials for study jenkins</h3>
1) https://medium.com/cloud-native-daily/jenkins-tutorial-basics-to-advanced-for-devops-engineer-27265e5ae67d

<h3>Deploy java-web-app with github-jenkins-maven and tomcat</h3>
https://medium.com/@mudasirhaji/deploy-a-java-web-app-with-github-jenkins-maven-and-tomcat-on-aws-step-by-step-process-f813c11c9930

<h3>Add jenkins slave node</h3> 
https://chathura-siriwardhana.medium.com/step-by-step-guide-to-add-jenkins-slave-nodes-f2e756c8849e

<h3>What is end to end testing ?(Lambdatest)</h3>
https://www.lambdatest.com/learning-hub/end-to-end-testing
- #!/usr/bin/env groovy

node {
    withEnv(["LT_USERNAME=Your LambdaTest UserName",
    "LT_ACCESS_KEY=Your LambdaTest Access Key",
    "LT_TUNNEL=true"]) {
 
        echo env.LT_USERNAME
        echo env.LT_ACCESS_KEY 
        
        stage('setup') { 
            // Get some code from a GitHub repository
            try {
                git 'https://github.com/LambdaTest/nightwatch-selenium-sample.git'
                
                // Download Tunnel Binary from the updated URL
                sh "wget https://downloads.lambdatest.com/tunnel/linux/64bit/LT_Linux.zip"
                
                // Download standalone unzip binary
                sh 'wget https://github.com/jcupitt/unzip-release/releases/download/v1.0/unzip-linux64 -O unzip'
                sh 'chmod +x unzip'
                
                // Use standalone unzip binary to unzip the file
                sh './unzip -o LT_Linux.zip'
                
                // Starting Tunnel Process 
                sh "./LT -user ${env.LT_USERNAME} -key ${env.LT_ACCESS_KEY} &"
                sh  "rm -rf LT_Linux.zip unzip"
            } catch (err) {
                echo err.toString()
            }
        }
        
        stage('build') {
            // Installing Dependencies
            sh 'npm install'
        }
        
        stage('test') {
            try {
                sh './node_modules/.bin/nightwatch -e chrome,edge tests'
            } catch (err) {
                echo err.toString()
            }
        }
        
        stage('end') {  
            echo "Success"
        }
    }
}

<h1>Jenkins Pipeline</h1>
tutorial for setup jenkins pipeline
- https://medium.com/@riteshshetty123/best-jenkins-pipeline-tutorial-for-beginners-examples-4c8a195876e6

<h2>Build process</h2>
tutorial for build java-app with maven (error in maven version not supported)
- https://www.jenkins.io/doc/tutorials/build-a-java-app-with-maven/




- #!/bin/bash
# This script installs Jenkins on an Ubuntu server

# Update package lists
sudo apt-get update

# Install Java 11
sudo apt-get install -y openjdk-11-jdk

# Download Jenkins key and add it to system
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null

# Add Jenkins to system package source list
sudo sh -c 'echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null'

# Update package lists again to include Jenkins and install it
sudo apt-get update
sudo apt-get install -y jenkins

# Verify Jenkins is installed and working
sudo systemctl status jenkins
