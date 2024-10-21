pipeline {
    agent any
    environment {
      MAVEN_ARGS=" -e clean install"
    }
    stages {
        stage('build') {
            steps {
               withMaven(maven: 'MAVEN_ENV') {
            		sh "mvn ${MAVEN_ARGS}"
       	       }
            }
        }
        stage('docker-compose start') {
        	steps{
        	timeout(time: 30, unit: 'SECONDS') {
                    sh 'docker compose up -d'
                }
                }
    	}
    }
}
