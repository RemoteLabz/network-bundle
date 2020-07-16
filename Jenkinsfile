pipeline {
    agent none
    stages {
        stage('Tests') {
            parallel {
                stage('Code quality') {
                    agent {
                        dockerfile true
                    }
                    steps {
                        sh 'composer install'
                        sh './vendor/bin/simple-phpunit --coverage-text --colors=never'
                    }
                }
                stage('Unit tests') {
                    agent {
                        dockerfile true
                    }
                    steps {
                        sh 'composer install'
                        sh './vendor/bin/phpcs --standard=PSR2 --exclude=Generic.Files.LineLength ./Entity/ ./Tests/'
                    }
                }
            }
            
        }
    }
}