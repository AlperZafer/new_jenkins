pipeline{
        agent any
        parameters {
        string(name: 'STACK_NAME', defaultValue:'example-stack', description: 'Enter the CloudFormation Stack Name.')
        string(name: 'PARAMETERS_FILE_NAME', defaultValue: 'example-stack-parameters.properties', description: 'Enter Parameters File Name')
        string(name: 'TEMPLATE_NAME', defaultValue: '01_s3cft.yml', description: 'Enter the CloudFormation Template File Name')
        choice(
            name: 'REGION',
            choices: [
                ' ',
                'us-east-1',
                'us-east-2',
                'us-west-2'
                ],
            description: 'AWS Account Region'
            )
    }
    stages {
        stage('Submit Stack'){
            steps{
                sh "aws cloudformation describe-stack-events --stack-name example-stack --region ${REGION}"
                sh "aws cloudformation deploy --stack-name ${STACK_NAME} --template-file ${TEMPLATE_NAME} --region ${REGION} --parameter-overrides file://${PARAMETERS_FILE_NAME}"
            }
        }
    }
}