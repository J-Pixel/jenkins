pipeline {
    agent { 
        node {
            label 'docker-agents-with-python'   #билд  только на агентах в докере с установленным питоном               
            }
      }
    triggers {
        pollSCM '*/5 * * * *'                   #тригер. проверять имзения репо каждые 5 минут
    }
    stages {
        stage('Build') {
            steps {                             #установка необходимых библиотек
                echo "Building.."
                sh ''' 
                cd myapp
                pip install -r requirements.txt 
                '''
            }
        }
        stage('Test') {                         #тестируем код с параметром и без
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name=Жан
                '''
            }
        }
        stage('Deliver') {                      #здесь могла быть отправка на сервер
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}
