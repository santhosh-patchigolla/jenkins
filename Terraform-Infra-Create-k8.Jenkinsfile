pipeline {
    agent any 
    parameters {
        choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Select The Environment')
    }
    options {
        ansiColor('xterm')    // Add's color to the output : Ensure you install AnsiColor Plugin.
    }
    stages {
        
        stage('Terraform Create Network') {
            steps {
                git branch: 'main', url: 'https://github.com/santhosh-patchigolla/terraform-vpc.git'
                sh "terrafile -f env-${ENV}/Terrafile"
                sh "terraform init --backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure"
                sh "terraform plan -var-file=env-${ENV}/${ENV}.tfvars"
                sh "terraform apply -var-file=env-${ENV}/${ENV}.tfvars -auto-approve"
            }
        }

        stage('Creating-EKS') {
            steps {
                dir('EKS') {  git branch: 'main', url: 'https://github.com/santhosh-patchigolla/Kubernetes1.git'

                        sh ''' 
                            cd eks 
                            make create
                            aws eks update-kubeconfig  --name ${ENV}-eks-cluster
                            kubectl get nodes
                        ''' 
                     }
                 }
            }
            
        // stage('Terraform Create Databases') {
        //     steps {
        //         git branch: 'main', url: 'https://github.com/b53-clouddevops/terraform-databases.git'
        //         sh "terrafile -f env-${ENV}/Terrafile"
        //         sh "terraform init --backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure"
        //         sh "terraform plan -var-file=env-${ENV}/${ENV}.tfvars"
        //         sh "terraform apply -var-file=env-${ENV}/${ENV}.tfvars -auto-approve"
        //     }
        // } 
    }
}