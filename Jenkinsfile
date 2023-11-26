pipeline {
    agent any

    parameters{
        string (name :'Env',defaultValue:'Test',description:'version to deploy')
        booleanParam(name: 'executetests', defaultValue: true, description: 'decide to run tc')
        choice(name: 'APPVERSION', choices: ['1.1', '1.2', '1.3'])
    }

    stages {
        stage('Compile') {
            steps {
                echo 'Compiling the code'
                echo "Compiling in ${params.Env}"
            }
        }
        stage('UnitTest') {
            when {
                expression{
                    params.executeTests ==true
                }
            }
            steps {
                echo 'testing the code'
            }
        }
        stage('Package') {
            steps {
                echo 'Packaging the code'
                echo "Packaging version ${params.APPVERSION}"
            }
        }
    }
}
