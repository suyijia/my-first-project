pipeline {
    agent any

    parameters {
        choice(
            name: 'BRANCH_NAME',
            choices: ['main', 'develop', 'feature'],
            description: '请选择要构建的 Git 分支'
        )
        booleanParam(
            name: 'RUN_TESTS',
            defaultValue: true,
            description: '是否执行测试阶段'
        )
        string(
            name: 'DEPLOY_ENV',
            defaultValue: 'dev',
            description: '请输入部署环境：dev / test / prod'
        )
    }

    stages {
        stage('获取代码') {
            steps {
                echo "拉取分支：${params.BRANCH_NAME}"
                // 你可以添加真正的 git checkout 命令
                // checkout scm，或用 git step
            }
        }

        stage('运行测试') {
            when {
                expression { return params.RUN_TESTS }
            }
            steps {
                echo '🧪 正在运行测试...'
                // 这里可以添加测试脚本命令
            }
        }

        stage('部署') {
            steps {
                echo "🚀 正在部署到环境：${params.DEPLOY_ENV}"
                // 执行部署相关脚本
            }
        }
    }
}
