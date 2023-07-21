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
//        stage('拉取源码') {
//            steps {
//                sh 'mkdir -p Serv_master'
//                dir("Serv_master") {
//                    git branch: 'master', url: 'https://github.com/SaintVamp/Serv.git'
//                }
//            }
//        }
//        stage('编译打包') {
//            steps {
//                sh '''
//                    cd Serv_master
//                    mvn package
//                '''
//            }
//        }

    }
    post('通知邮件') {
        always {
            script {
                emailext(subject: '接口自动化测试结果',
                        body: '效果不错',
                        to: 'wp2sy001@163.com',)
            }
        }
    }
}