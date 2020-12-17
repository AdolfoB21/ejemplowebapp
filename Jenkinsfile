pipeline{
    agent any
    stages{
        stage('Repositorio'){
            steps{
                echo 'Repositorio'
                git url: 'https://github.com/AdolfoB21/ejemplowebapp.git'
            }
        }
        stage('Empaquetado'){
            steps{
                echo 'Empaquetado Maven'
                sh 'mvn package'
                sh 'exit 0'
            }
        }
        stage('Tomcat'){
            steps{
                echo 'Tomcat'
                deploy adapters: [tomcat9(credentialsId: 'a4dafd37-c5e9-43cb-bbcf-f6658541fcf6', path: '', url: 'http://localhost:8082')], contextPath: 'prueba1', war: 'target/miweb.war'
            }
        }
    }
    post{
        always{
            echo 'Yo me ejecuto siempre'
        }
        success{
            echo 'Yo me ejecuto cuando todo ha ido bien'
        }
        failure{
            echo 'Yo me ejecuto cuando ha ido mal'
        }
        changed{
            echo 'Yo me ejecuto si esta ejecución no acaba en el mismo estado que la anterior ejecucion'
        }
    }
}