pipeline {
    agent any

    parameters {
        choice(
            name: 'BRANCH_NAME',
            choices: ['main', 'develop', 'master'],
            description: '请选择要构建的 Git 分支'
        )
    }

    environment {
        // 定义一个变量用于打印、部署路径等用途
        PROJECT_NAME = 'my-demo-app'
    }

    stages {
        stage('拉取代码 (Checkout)') {
            steps {
                echo "从 Git 仓库拉取分支：${params.BRANCH_NAME}"
                git branch: "${params.BRANCH_NAME}", url: 'https://github.com/your-name/your-repo.git'
            }
        }

        stage('构建 (Build)') {
            steps {
                echo "构建项目 ${env.PROJECT_NAME} ..."
                // 假设是 Node 项目：npm install
                bat 'echo 模拟构建命令，例如 npm install 或 mvn clean install'
            }
        }

        stage('测试 (Test)') {
            steps {
                echo '运行测试...'
                // 模拟测试
                bat 'echo 这里运行测试命令'
            }
        }

        stage('部署 (Deploy)') {
            steps {
                echo "部署分支：${params.BRANCH_NAME}"
                // 模拟部署
                bat 'echo 模拟部署命令'
            }
        }
    }
