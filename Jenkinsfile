pipeline {
    agent any
    stages{
        stage('stage one') {
            steps {
                    sh '''
                        echo devops
                        echo aws
                        echo batch 54
                    '''
            }
        }
        stage('stage two') {
            steps {
                echo "this is stage two" 
            }
        } 
        stage('stage three') {
            steps {
                echo "this is stage three" 
            }
        }               
    }
}

