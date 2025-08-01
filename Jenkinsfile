pipeline {
    agent any

    parameters {
        choice(
            name: 'BRANCH_NAME',
            choices: ['main', 'develop', 'feature-x'],
            description: '请选择要构建的 Git 分支'
        )
        booleanParam(
            name: 'RUN_TESTS',
            defaultValue: true,
            description: '是否运行测试用例'
        )
        choice(
            name: 'BUILD_MODE',
            choices: ['Debug', 'Release'],
            description: '构建模式选择'
        )
    }

    environment {
        PROJECT_NAME = 'my-demo-app'
    }

    stages {
        stage('拉取代码') {
            steps {
                echo "从 Git 仓库拉取分支：${params.BRANCH_NAME}"
                git branch: "${params.BRANCH_NAME}", url: 'https://github.com/your-name/your-repo.git'
            }
        }

        stage('构建') {
            steps {
                echo "构建模式：${params.BUILD_MODE}"
                bat "echo 构建项目 ${env.PROJECT_NAME}，模式为 ${params.BUILD_MODE}"
            }
        }

        stage('测试') {
            when {
                expression { return params.RUN_TESTS }
            }
            steps {
                echo '开始运行测试...'
                bat 'echo 执行测试命令...'
            }
        }

        stage('部署') {
            when {
                anyOf {
                    branch 'main'
                    branch 'develop'
                }
            }
            steps {
                echo "部署分支：${params.BRANCH_NAME}"
                bat 'echo 模拟部署操作...'
            }
        }
    }
}
