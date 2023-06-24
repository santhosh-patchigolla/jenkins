pipeline {
    agent any
    environment { 
        ENV_URL = 'pipeline.google.com'    # its a pipeline variable every stage can use it by using a variable
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
            steps {
                echo "this is stage two" 
                echo "URL name is ${ENV_URL}"
            }
        } 
        stage('stage three') {
            steps {
                echo "this is stage three" 
            }
        }               
    }
}

