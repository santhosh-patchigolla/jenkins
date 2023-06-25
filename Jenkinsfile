pipeline {
    agent any
    environment { 
        ENV_URL         = "pipeline.google.com"    //  its a pipeline variable every stage can use it by using a variable
        SSHCRED         = credentials('SSH_CRED')  // took from manage jenkins> security> credentials  (here we can store the secrets in the jenkins)
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Varma', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['Dev', 'NonProd', 'Prod'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }  
    triggers { pollSCM('H/1 * * * *') }     
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
                echo "This is a stage three"
                echo "URL name is ${ENV_URL}"
                echo -e "\\e[33m hello"

                ''' 
            }
        }                                          
    }
}