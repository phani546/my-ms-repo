pipeline {
	agent any
	//agent { docker { image 'node:13.8'} }
	environment {
		dockerHome= tool 'mymaven'
		mavenHome= tool 'mydocker'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
           steps{
			   sh 'mvn --version'
			   sh 'docker version'
		   }
		}
		stage('Build'){
           steps{
			   sh 'mvn clean compile'
		   }
		}
		stage('Test'){
           steps{
			   sh 'mvn test'
		   }
		}
		stage('Integration Test'){
           steps{
			   echo 'mvn failsafe:integration-test failsafe:verify'
		   }
		}
		stage('Package'){
           steps{
			   echo 'mvn package -DskipTests'
		   }
		}
		stage('Build Docker Image'){
            steps{
			   script{
			    docker.build("psn546/currency-exchange-devops:${env.BUILD_TAG}")
			   }
		    }
		}
        stage('Push Docker Image'){
			steps{
				script{
					docker.withRegistry('','dockerhub')
					dockerImage.push();
					dockerImage.push('latest');
				}
			}
		}

	}
	post{
		always{
			echo 'I run always'
		}
		success{
			echo 'I run when you are successful'
		}
		failure{
			echo 'I run when failure'
		}

		changed{
			echo 'I run when u fail'
		}
	}
}
