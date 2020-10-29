pipeline {
	agent any
	//agent { docker { image 'node:13.8'} }
	stages{
		stage('Build'){
           steps{
			   //sh 'mvn --version'
			   //sh 'node --version'
			   echo "Build"
			   echo "$PATH"
			   echo "BUILD_NUMBER - $env.BUILD_NUMBER"
			   echo "BRANCH_NAME - $env.BRANCH_NAME"
			   echo "CHANGE_AUTHOR - $env.CHANGE_AUTHOR"
			   echo "JOB_URL - $env.JOB_URL"
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
