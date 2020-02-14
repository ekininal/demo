pipeline{
    agent any
    stages{
        stage("build"){
            steps{
				sh '$(aws ecr get-login --no-include-email --region eu-central-1)'
				sh 'docker build -t demo .'
				sh 'docker tag demo:latest 198729827487.dkr.ecr.eu-central-1.amazonaws.com/demo:latest'
				sh 'docker push 198729827487.dkr.ecr.eu-central-1.amazonaws.com/demo:latest'
				sh 'aws ecs update-service --cluster demo --region eu-central-1 --service demo --task-definition demo:1'
            }
        }
    }
}
