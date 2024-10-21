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
        	timeout(time: 3, unit: 'HOURS') {
                    sh 'docker compose up -d'
                }
    	}
    }
}
