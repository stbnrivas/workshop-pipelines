#!groovy

pipeline {
    agent {
        // how the pipeline will be built
        image 'adoptoopenjdk/openjdk11:jkd-11.0.3_7'
        args '--network ci --mount type=volume,source=ci-maven-home,target=/root/.m2'
    }

    environment {
        // properties or environment variables, new or derived
        ORG_NAME = "deors"
        APP_NAME = "workshop-pilelines-stbn"
        APP_CONTEXT_ROOT = "/8080"
        TEST_CONTAINER_NAME = "ci-${APP_NAME}-${BUILD_NUMBER}"
        DOCKER_HUB = credentials("${ORG_NAME}-docker-hub")
    }

    stages {
        
        stage('Compile') {
            steps {
                // steps for stage 1 come here
                echo "-=- compiling project -=-"
                sh "./mvnw clean compile"
            }
        }

    }

    post {
        // post-process activities, e.g. cleanup or publish
    }
}
