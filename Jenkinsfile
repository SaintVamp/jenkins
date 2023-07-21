pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'jdk17.0.8'
    }
    stages {

        stage('输出版本号') {
            steps {
                sh "java -version"
                sh "mvn -v"
                echo "________________________"
                echo "++++++++++++++"

            }
        }
        stage('拉取源码') {
            steps {
                sh 'mkdir -p Serv_master'
                dir("Serv_master") {
                    git branch: 'master', url: 'https://github.com/SaintVamp/Serv.git'
                }
            }
        }
        stage('编译打包') {
            steps {
                sh '''
                    cd Serv_master
                    mvn package
                '''
            }
        }

    }
    post('通知邮件') {
        always {
            emailext(body: '${DEFAULT_CONTENT}',
                    subject: '${DEFAULT_SUBJECT}',
                    from: '${DEFAULT_RECIPIENTS}',
                    to: '${DEFAULT_RECIPIENTS}')
        }
    }
}