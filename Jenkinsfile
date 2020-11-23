pipeline {
  agent any
  stages {
    stage ('Ansible-Server - Checkout') {
 	    steps {
 	      checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GIT-PESSOAL-DANILO', url: 'https://github.com/daniloliebel/ansible-awx.git']]]) 
 	    }
 	  }
 	  stage ('Build'){
 	    parallel {
 	      stage ('Ansible Task') {
 	        steps {
            script {
              DOCKER_HOME = "${tool 'docker'}"
              env.PATH = "${DOCKER_HOME}/bin:${env.PATH}"
              println env.PATH
              sh '''
                 docker build -t kmmeng/ansible-task:${BUILD_NUMBER} --build-arg ANSIBLE_VERSION=${ANSIBLE_VERSION} task/
                 docker login -u daniloliebel -pV1129power!
                 docker push kmmeng/ansible-task:${BUILD_NUMBER}
                 docker rmi -f kmmeng/ansible-task:${BUILD_NUMBER}
                 '''
            }
 	        }
 	      }
 	      stage ('Ansible Redis') {
 	        steps {
            script {
              DOCKER_HOME = "${tool 'docker'}"
              env.PATH = "${DOCKER_HOME}/bin:${env.PATH}"
              println env.PATH
              sh '''
                 docker build -t kmmeng/ansible-redis:${BUILD_NUMBER} redis/
                 docker login -u daniloliebel -pV1129power!
                 docker push kmmeng/ansible-redis:${BUILD_NUMBER}
                 docker rmi -f kmmeng/ansible-redis:${BUILD_NUMBER}
                 '''
            }
 	        }
 	      }
 	      stage ('Ansible Web') {
 	        steps {
            script {
              DOCKER_HOME = "${tool 'docker'}"
              env.PATH = "${DOCKER_HOME}/bin:${env.PATH}"
              println env.PATH
              sh '''
                 docker build -t kmmeng/ansible-awx:${BUILD_NUMBER} --build-arg ANSIBLE_VERSION=${ANSIBLE_VERSION} web/
                 docker login -u daniloliebel -pV1129power!
                 docker push kmmeng/ansible-awx:${BUILD_NUMBER}
                 docker rmi -f kmmeng/ansible-awx:${BUILD_NUMBER}
                 '''
            }
 	        }
 	      }
 	    }
    }
  }
}
