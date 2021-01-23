pipeline {
    agent {label 'dev'}
	
	   
    stages {
        stage('Two') {
                steps {
                        echo 'Hi, this is Raymond from FDA'
			
                }
        }
	    stage('Three'){
		    
		steps {
			input('Do you want to proceed?')
        }
	    }
        stage('Four') {
                when {
                        not {
                                branch "master"
                        }
                }
                steps {
			echo "Hello"
                        }
        }
        stage('Five') {
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
