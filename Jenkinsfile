pipeline {
    agent any
    environment {
        Course = "joindevops"
    }
    options {
        timeout(time: 5, unit: "MINUTES")
        disableConcurrentBuilds()
    }
    parameters{
        string(name: "PERSON", defaultValue: "raheem")
         text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
    booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages{
        stage('build') {
            steps{
                script {
                    sh """
                        echo "hello world"
                        // sleep 10
                        env
                        env.Course
                        ${env.Course}
                        echo "hello ${params.PERSON}"
                        """
                }
            }
        }
        stage('test'){
            steps{
                script{
                    echo "testing"
                }
            }
        }
        stage("deploy") {
            input {
                message "should we cont"
                ok "yes"
                submitter "stopped"
                parameters {
                    string(name: 'PERSON', defaultValue: 'sameer')
                }

            }
            steps{
                script {
                    echo "hello ${PERSON}, hi"
                    echo "deploying"
                }
            }
        }
    }
    post {
        always {
            echo "i always run dude"
            deleteDir()

        }
        success {
            echo "success"
        }
        failure {
            echo "failed"
        }
    }




}

