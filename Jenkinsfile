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


        stage('c') {
            steps {
                sleep 1
            }
        }
        stage('通知邮件') {
            steps {
                emailext(body: '$DEFAULT_CONTENT',
                        recipientProviders: [[$class: 'RequesterRecipientProvider']],
                        subject: '$DEFAULT_SUBJECT',
                        to: 'wp2sy001@163.com',
                        from: 'wp2sy001@163.com')
            }
        }

    }
}