pipeline {
    agent any
    environment { 
        ENV_URL = "pipeline.google.com"    //  its a pipeline variable every stage can use it by using a variable
    }    
    stages{
        stage('stage one') {
            steps {
                    sh '''
                        echo devops
                        echo aws
                        echo batch 54
                        echo URL name is ${ENV_URL}
                    '''
            }
        }
        stage('stage two') {
            environment {                            
                ENV_URL = "stage.google.com"              // this is a stage level (local) varible it can be used on this stage only
            }                        
            steps {
                echo "this is stage two" 
                echo "Name of the URL is ${ENV_URL}"     
            } 
        }                           
    }
}