pipeline {
    agent {
        kubernetes {
           idleMinutes 5  // how long the pod will live after no jobs have run on it
           yamlFile 'jenkins-pods.yaml'  // path to the pod definition relative to the root of our project
           defaultContainer 'main'  // define a default container if more than a few stages use it, will default to jnlp container
        }
    }
    stages {
        stage('Main') {
            steps {
                script {
                  sh """
                    echo Running
                    if [ FAIL_JOB = "true" ]; then
                        exit 30
                    else
                        echo "JOB completed"
                    fi
                  """
                }
            }
        }
    }
}
