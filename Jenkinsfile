pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
		checkout scm
	    }
	}
	stage('Build') {
	    steps {
		sh '/home/gamut/distros/apache-maven-3.6.1/bin/mvn install'
	}
	    }
	stage('Deployment') {
	    steps {
		sh  'cp target/gamutkart.war /home/gamut/distros/apache-tomcat-8.5.42/webapps'
		sh '"JAVA_HOME=/home/gamut/distros/jdk1.8.0_211" "/home/gamut/distros/apache-tomcat-8.5.42/bin/startup.sh"'
	    }
	}

    }
}
