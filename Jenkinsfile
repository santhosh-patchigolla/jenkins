pipeline {
    agent {
        label 'work-station'
    }
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
        stage('Parallel Stages') {                      // this parallel stage will insure to runn stages paralled refer the stage name as parallel1 parallel2.
        parallel {
            stage('In Parallel 1') {
                    steps {
                        echo "In Parallel 1"
                        sh "sleep 2"
                        sh "hostname"
                    }
                }
            stage('In Parallel 2') {
                    steps {
                        echo "In Parallel 2"
                        sleep 2
                }
            }
            stage('In Parallel 3') {
                    steps {
                        echo "In Parallel 3"
                        sleep 2
                }
            }
        }
    }    
        stage('Stage One') {
            steps {    
                    sh '''
                        echo DevOps Training
                        echo cloud Training
                        echo new batch
                        echo Name of the URL is ${ENV_URL}
                        
                        env

                    '''
            }
        }

        stage('Stage TWO') {
            environment {
                ENV_URL = "stage.google.com"                  // Stage  variables declared here if we declared here means It wont take from pipeline variable(global varailble)
            }

            // input {                                            // using this input we can break the state and ask for the valuer once you give it will run the stage of the pipeline. Usually this is used if this stage createing any changes to the Infra they need to acknowledged.
            //     message "Are you interested to continue?"
            //     ok "Yes, we should."
            //     submitter "alice,bob"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'santhosh', description: 'Who should I say Hi to?')
            //     }

            // }            
            steps {                 
                echo  "This is stage two"

            }
        }

        stage('Stage THREE') {
            when { 
                 branch 'dev'
                 changeset "**/*.js" 
            }        // this when is useful only it should run the stage only on the specfic branch and the "changeset" is useful it notice any changes on the  .js file"
            steps {                 
                sh ''' 
                echo "This is stage three"
                echo "Name of the URL is ${ENV_URL}"
                sleep 5

                ''' 
            }
        }            
        
        stage('Stage four') {
            steps {                 
                sh ''' 
                echo "This is stage four"
                echo "Name of the URL is ${ENV_URL}"
                sleep 5

                ''' 
            }
        }        
    }

    post {                                         // This post will show that all the jobs are excuted its a kind of our reference and this "post" should be at the end of all the stages FYU refer readme file
        aborted { 
            echo 'I will always say Hello if its aborted!'
        }
    }    

}

// no changes added but this change will run the Jenkins job.



