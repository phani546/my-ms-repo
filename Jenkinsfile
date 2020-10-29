pipeline {
	//agent any
	agent { docker { image 'maven:3.6.3'} }
	stages{
		stage('Initialize'){
           def dockerHome = tool 'mydocker'
           env.PATH = "${dockerHome}/bin:${env.PATH}"
        }  
		stage('Build'){
           steps{
			   echo 'mvn --version'
			   echo "Build"
		   }
		}
		stage('Test'){
           steps{
			   echo('Test')
		   }
		}
		stage('Integration Test'){
           steps{
			   echo('Integration Test')
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
