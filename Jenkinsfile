pipeline {
  agent any

  options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
  }

  tools {nodejs 'nodeJs'}

  stages {

    stage('Cloning Git') {
      steps {
        git branch: 'master',
        credentialsId: 'noble_dubai',
        url: 'https://nibuae@bitbucket.org/nibuae/noble_dubai_ui.git'
      }
    }

    stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
         // sh 'npm test'
         echo "This is Test Stage"
      }
    }

    stage('Build') {
      steps {
        sshagent(['noble_production']) {
         // sh 'npm build --prod'
         echo "************* Starting build !!!*************"
         sh 'ls -lah'
         sh 'pwd'
         sh 'npm run-script build --prod --aot'
         echo "************* Copying Build Artifact to ec2 machine*************"
         sh 'scp -r -o StrictHostKeyChecking=no dist ubuntu@ec2-18-197-207-55.eu-central-1.compute.amazonaws.com:~/Softwares/Artifact/dist-$BUILD_NUMBER-$(date +%Y%m%d)'
      }
      }
    }


    stage('Deploy'){
    steps{
        sshagent(['noble_production']) {

          echo "************* Login to noble_dubai production server *************"
          echo ""
          //echo "*************Hostname is $hostname*************"
          //echo ""
          //echo "User is : $whoami"
          //echo ""
          echo "************* STARTING DEPLOYMENT !!! *************"
          sh 'scp -r -o StrictHostKeyChecking=no dist/* ubuntu@ec2-18-197-207-55.eu-central-1.compute.amazonaws.com:~/Softwares/tomcat9/webapps/ROOT/'
          echo "************* DEPLOYMENT COMPLETE !!! *************"
          }
        }
      }

      stage('Restart Server'){
      steps{
          sshagent(['noble_production']) {
          echo "************* Connecting to Application Server !!! *************"
          echo " "
          sh "ssh -o StrictHostKeyChecking=no ubuntu@ec2-18-197-207-55.eu-central-1.compute.amazonaws.com 'sh ~/Softwares/scripts/restart_tomcat.sh'"
          echo "************* Restart Complete !!!*************"
          }
        }
      }

  }
}
