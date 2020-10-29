pipeline {
	agent any
	//agent { docker { image 'node:13.8'} }
	environment {
		dockerHome= tool 'mymaven'
		mavenHome= tool 'mydocker'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Build'){
           steps{
			   sh 'mvn --version'
			   sh 'docker version'
		   }
		}
		stage('Test'){
           steps{
			   echo('Test')
		   }
		}
		stage('Integration Test'){
           steps{
			   echo('Integration Tests')
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
