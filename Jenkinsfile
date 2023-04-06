pipeline {
    agent any

    stages {
        stage('GIT CHECKOUT') {
            steps {
                git branch: 'main', url: 'https://github.com/abhayychaudharyy/webinar.git'
            }
        }

        stage('UNIT TESTING') {
            steps {
                sh 'mvn test'
            }
        }

        stage('INTEGRATION TESTING') {
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
        }
        
        stage('MAVEN BUILD') {
            steps {
                sh 'mvn clean install'
            }
        }
        /*
      stage('STATIC CODE ANALYSIS') {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'sonarqubetoken') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        stage('QUALITY GATE STATUS') {
            steps {
                script {
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonarqubetoken'
                }
            }
        }
        stage('Upload Artifacts to Nexus'){
            
            steps{
                script{
                    nexusArtifactUploader artifacts: 
                [
                    [
                    artifactId: 'springboot',
                    classifier: '', 
                    file: 'target/Thapar.jar', 
                    type: 'jar'
                    ]
                ], 
                    credentialsId: 'nexuscreds', 
                    groupId: 'com.example', 
                    nexusUrl: '54.209.100.177:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'java-release', 
                    version: '1.0.0'
                }
            }
        }
        /*stage("Docker Image Build"){
            steps {
                script {
                    sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID .'
                    sh 'docker image tag $JOB_NAME:v1.$BUILD_ID vishalchauhan9/$JOB_NAME:v1.$BUILD_ID'
                    sh 'docker image tag $JOB_NAME:v1.$BUILD_ID vishalchauhan9/$JOB_NAME:latest'
                }
            }
        }
        stage("Push Docker Image to Docker HUB"){
            steps {
                script {
                    
                    withCredentials([string(credentialsId: 'dockerhub_password', variable: 'dockerhub_creds')]) {
                        sh 'docker login -u vishalchauhan9 -p ${dockerhub_creds}'
                        sh 'docker image push vishalchauhan9/$JOB_NAME:v1.$BUILD_ID'
                        sh 'docker image push vishalchauhan9/$JOB_NAME:latest'
                    }
                }
            }
        }*/
    }
}