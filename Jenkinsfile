pipeline {
    agent any

    stages {
    
        stage('Initialize') {
            steps {          	
				sh "./gradlew build"
				sh "init"
                echo "The pipeline stage Initialized successfully."
            }
        }


     	stage('Functional Tests') {
	        steps {
	            sauce('9feb84045-449f-47b5-99c6-3d5c0c5a7be7') {
						sh "./gradlew clean test"
						//step([$class: 'SauceOnDemandTestPublisher'])    
		            	echo "The pipeline stage Functional Tests completed successfully."                    
	            	   
	            }
	        }
        }


        stage('Sauce Reporting') {
            steps {
                echo "The pipeline stage Reporting completed successfully."
                step([$class: 'SauceOnDemandTestPublisher'])
                saucePublisher()
            }
        }

        stage('Clean') {
            steps {
                echo "The pipeline stage Clean completed successfully."
            }
        }
        


    }
    
}