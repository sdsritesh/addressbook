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
                    params.executetests == true
                }
            }
            steps {
                echo 'testing the code'
            }
        }
        stage('Package') {
            input {
                message "Select the version to package"
                ok "Version Selected"
                parameters {
                    choice(name: 'NEWAPP', choices: ['1.2', '2.1', '3.1'])
                }
            }

            steps {
                echo 'Packaging the code'
                echo "Packaging version ${params.APPVERSION}"
            }
        }
    }
}
