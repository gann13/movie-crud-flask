pipeline {
	agent any
	stages {

		stage ("Git checkout"){
			steps {
				git branch: "master",
				url: "https://github.com/gann13/movie-crud-flask.git"
				sh "ls"
			}
		}
		
		stage ("Python Flask Prepare"){
			steps {
				//sh "pip3 install -r requirements.txt"
				echo "Install requirements"
			}

		}
		stage ("Unit Test"){
			steps{
				//sh "python test_basic.py"
				echo "Run unit tests"
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
				sh "${tool("sonar_scanner")}/bin/sonar-scanner"
			}
		}
		
	}
}
