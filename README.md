pipeline{
    agent any
    stages {
        stage ('stage one')
        steps {
            echo "this is step one"
        }
    }

}