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
		sh 'sshpass -p "gamut" scp target/gamutkart2.war gamut@172.17.0.2:/home/gamut/distros/apache-tomcat-8.5.42/webapps'
		sh 'sshpass -p "gamut" ssh gamut@172.17.0.2 "JAVA_HOME=/home/gamut/distros/jdk1.8.0_211" "/home/gamut/distros/apache-tomcat-8.5.42/bin/startup.sh"'
	    }
	}

    }
}

