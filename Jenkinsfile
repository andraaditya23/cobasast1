pipeline {
	agent any
	stages {
		stage ("Git checkout"){
			steps {
				git branch: "master",
					url: "https://github.com/andraaditya23/cobasast1.git"
				sh "ls"
			}
		}
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
				sh "bandit --exit-zero -r ."
			}
		}
		stage ("Dependency Check with Python Safety"){
			steps{
				sh "safety check -i *"
				sh "safety check --json > report.json"
			}
		}
		stage ("Static Analysis with python-taint"){
			steps{
				sh "pyt ."
			}
		}					
	}
}
