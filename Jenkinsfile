pipeline {
agent {
     node ('devops')
    }

    
    stages {
        stage('build vm') {
        steps {
        sh 'ansible-playbook /etc/ansible/playbooks/build_bluegreen.yaml'
            }
            }
        stage('build container') {
        steps {
        sh 'ansible-playbook /etc/ansible/playbooks/container_bluegreen.yaml'
               }
               
               }
               
        stage('deploy app') {
        steps {
        sh 'ansible-playbook /etc/ansible/playbooks/deploy_bluegreen.yaml'
        
               }
                         }
        
        stage('test app container') {
        input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
        steps{
        sh 'ansible-playbook /etc/ansible/playbooks/test_bluegreen.yaml'
            }
        
                                    }
        stage('deploy prod'){
        steps{
        sh 'ansible-playbook /etc/ansible/playbooks/prod_bluegreen.yaml'
              }
        
                            }
        
        
            }
        
        
        
 }

