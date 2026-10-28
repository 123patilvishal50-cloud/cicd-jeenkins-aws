node{
    def appDir = /var/www/html/

    stage('clean workspace'){
        echo "Cleaning workspace"
        deleteDir()
    }

    stage('clone repository'){
        echo 'Cloning repository'
        git(
            branch: 'main',
            url: 'https://github.com/123patilvishal50-cloud/cicd-jeenkins-aws'        )
    }



    stage('deploy to ec2'){
        echo 'Deploying to ec2'
        sh " " "
            sudo mkdir -p ${appDir}
            sudo chown -R jenkins ${appDir}

            sync -avz --delete --exclude='git' --exclude='Jenkinsfile' ./ ${appDir}

            cd ${appDir}
            sudo npm install
            sudo npm run build
            sudo fuster -k 3000/tcp ||
            true
            npm run start
        " " "
    }
    
}