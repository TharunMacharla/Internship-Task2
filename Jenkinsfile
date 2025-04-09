pipeline{
    agent any
    stages{
        stage('clone'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/TharunMacharla/Petclinic.git']])
            }
        }
        stage('validate'){
            steps{
                sh  'mvn validate'
            }
        }
        stage('compile'){
            steps{
                sh  'mvn compile'
            }
        }
        stage('test'){
            steps{
                sh  'mvn test'
            }
        }
        stage('package'){
            steps{
                sh  'mvn package'
            }
        }
        stage('docker image build'){
            steps{
                sh 'docker build -t vmr1 .'
                sh 'docker run --name myc2 -d -p 8083:8080 devopsvmr/vmr1 .'
            }
        }
    }
}
