pipeline {
	agent any
	stages {

		stage ("Python Flask Prepare"){
			steps {
				sh "pip3 install -r requirements.txt"
			}

		}
		stage ("Unit Test"){
			steps{
				sh "python3 test_basic.py"
			}
		}
		stage ("Python Bandit Security Scan"){
			steps{
				sh "cat report/banditResult.json"
				sh "sh run_bandit.sh || true"
				sh "ls"
			}
		}


		stage ("sonar-publish"){
			steps {
				echo "===========Performing Sonar Scan============"
				sh "${tool("sonarqube")}/bin/sonar-scanner"
			}
		}
		
	}
}
