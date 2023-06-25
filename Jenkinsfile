pipeline {
    agent any
    environment { 
        ENV_URL         = "pipeline.google.com"    //  its a pipeline variable every stage can use it by using a variable
        SSHCRED         = credentials('SSH_CRED')  // took from manage jenkins> security> credentials  (here we can store the secrets in the jenkins)
    }   
    stages{
        stage('stage one') {
            steps {
                    sh '''
                        echo devops
                        echo aws
                        echo batch 54
                        echo URL name is ${ENV_URL}

                        env
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

        stage('Stage THREE') {
            steps {                 
                sh ''' 
                echo "This is stage three"
                echo "Name of the URL is ${ENV_URL}"
                echo -e "\\e[31m Hai"

                ''' 
            }
        }                                          
    }
}