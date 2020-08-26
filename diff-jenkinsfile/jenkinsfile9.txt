pipeline {
    agent any
    stages {
        stage('One') {
                steps {
                        echo 'Hi, this is Zulaikha from edureka'
			
                }
        }
	    stage('Two'){
		    
		steps {
			input('Do you want to proceed?')
        }
	    }
        stage('Three') {
                when {
                        not {
                                branch "master"
                        }
                }
                steps {
			echo "Hello"
                        }
        }
        stage('Four') {
                parallel {
                        stage('Unit Test') {
                                steps{
                                        echo "Running the unit test..."
                                }
                        }
                        stage('Integration test') {
                        agent {
                                docker {
                                        reuseNode false
					image 'onyima101/mynode:1.0' ##'onyima101/nginx-assessment:v1.2'##
                                        }
			}
				steps {
					echo 'Running the integration test..'
				}
                               
			}  }
        }
    }
}

