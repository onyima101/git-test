pipeline {
    agent dev
    stages {
        stage('One') {
                steps {
                        echo 'Hi, this is Raymond from FDA'
			
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
					image 'onyima101/mynode:1.0' 
                                        }
			}
				steps {
					echo 'Running the integration test..'
				}
                               
			}  }
        }
    }
}
