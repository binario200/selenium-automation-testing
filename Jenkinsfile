#!/usr/bin/env groovys

pipeline {
    agent any

    stages {
        stage ('Clone') {
          steps {
            git url: 'https://github.com/ksqartechinc/selenium-automation-testing.git', branch: 'master'
          }
        }

          // agent {
          //     docker {
          //         image 'maven:3-alpine'
          //         args '-v /root/.m2:/root/.m2'
          //         reuseNode true
          //     }
          // }
          tools {
            maven 'Maven 3.5.2'
          }

          steps {
                sh 'mvn -B -DskipTests clean package'
                sh 'docker images'
                // CHK maybe targe will be loose after mvn clean package
                // stash will be required
          }
        }

        /*
        stage('Build Docker Image') {
          agent {
            dockerfile true
            //reuseNode true
          }

          steps {
            // building the docker image
            // sh 'docker build -t "infolob/GapOracleEBsTest:${env.BUILD_ID}"'
            //docker.build("infolob/GapOracleEBsTest:${env.BUILD_ID}")
          }

        }

        stage('Running Tests') {
            steps {
              // running the docker image with the tests
              // testingImage.inside {
              //     sh '/usr/bin/java -cp /usr/share/tag/container-test.jar org.testng.TestNG /usr/share/tag/basic-flow-module.xml'
              // }
            }

        }


        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS'
              }
            }
            steps {
                //testingImage.push('latest')
            }
        }
        */
    }

}
