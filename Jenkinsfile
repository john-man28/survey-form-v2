pipeline {
    agent any

    stages {
        stage('Build and Test') {
            steps {
                script {
                    def yaml = readYaml file: 'path/to/your/github/actions.yml'
                    sh "docker-compose -f ${yaml.jobs.build.steps[2].run} up -d --build"
                    sh "docker run survey-form-v2 sh -c '${yaml.jobs.build.steps[3].run}'"
                    sh "docker-compose -f ${yaml.jobs.build.steps[4].run} down"
                }
            }
        }
    }
}