pipeline {
    agent any
    environment{
        NEW_VERSION= '1.0.0'
    }
    
    tools{
        maven 'Maven'
    }
    
    parameters{
        choice(name: 'VERSION', choices: ['1.1.0','1.2.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }

    stages {
        stage('build') {
            steps {
                echo 'built successfully'
                echo "building version ${NEW_VERSION}"
                bat 'mvn install'
            }
        }
        stage('test') {
            when{
                expression{
                    params.executeTests
                }
            }
            steps {
                echo 'tested successfully'
            }
        }
        stage('deploy') {
            steps {
                echo 'deployed successfully'
                echo "deploying version ${params.VERSION}"
            }
        }
    }
}
