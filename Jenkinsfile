pipeline {
    agent any
    environment {
        ENV_URL         = "pipeline.google.com"                  //  its a pipeline variable every stage can use it by using a variable
        SSHCRED         = credentials('SSH_CRED')                // took from manage jenkins> security> credentials  (here we can store the secrets in the 
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['Dev', 'NonProd', 'Prod'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    // triggers { pollSCM('*/1 * * * *') }

    stages {
        stage('Stage One') {
            steps {    
                    sh '''
                        echo DevOps Training
                        echo AWS Training
                        echo Batch54
                        echo Name of the URL is ${ENV_URL}
                        
                        env

                    '''
            }
        }

        stage('Stage TWO') {
            environment {
                ENV_URL = "stage.google.com"                  // Stage  variables declared here if we declared here means It wont take from pipeline variable(global varailble)
            }

            input {                                            // using this input we can break the state and ask for the valuer once you give it will run the stage of the pipeline. Usually this is used if this stage createing any changes to the Infra they need to acknowledged.
                message "Are you interested to continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'santhosh', description: 'Who should I say Hi to?')
                }

            }            
            steps {                 
                echo  "This is stage two"
            }
        }
        
        stage('Stage THREE') {
            when { 
                branch 'main'
            }
            steps {                 
                sh ''' 
                echo "This is stage three"
                echo "Name of the URL is ${ENV_URL}"

                ''' 
            }
        }            
            steps {                 
                sh ''' 
                echo "This is stage three"
                echo "Name of the URL is ${ENV_URL}"


                ''' 
            }
        }

        stage('Stage four') {
            steps {                 
                sh ''' 
                echo "This is stage three"
                echo "Name of the URL is ${ENV_URL}"


                ''' 
            }
        }        
    }
}

// no changes added but this change will run the Jenkins job.