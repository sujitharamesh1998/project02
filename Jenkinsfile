node{
    stage('git code checkout'){
        echo 'checkout the code from git repository'
        git 'https://github.com/sujitharamesh1998/project02'
        echo 'completed'
        }
    stage('build'){
        sh "mvn clean package"
    }
     stage('docker'){
        sh "docker build -t project02 ."
    }
    stage('login'){
    withCredentials([string(credentialsId: 'dockerhubpass', variable: 'docker')]) {
    sh " docker login -u sujitha202301 -p ${docker}"
       }
    }
    stage('tag'){
        sh " docker tag project02 sujitha202301/staragileproject:2"
        sh " docker push sujitha202301/staragileproject:2 "
    }
}   
