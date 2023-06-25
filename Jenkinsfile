pipeline {
    agent any
    environment {
        ENV_URL         = "pipeline.google.com"                  // Pipeline variable
        SSHCRED         = credentials('SSH_CRED') 
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    triggers { pollSCM('*/1 * * * *') }

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
                ENV_URL = "stage.google.com"                  // Stage  variab declared here
            }
            steps {                 
                echo  "This is stage two"
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