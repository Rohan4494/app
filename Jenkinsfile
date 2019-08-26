podTemplate(label: label, containers: [
//   containerTemplate(name: 'git', image: ‘alpine/git‘, ttyEnabled: true, command: ‘cat’),
//   containerTemplate(name: 'maven', image: ‘maven:3.3.9-jdk-8-alpine’, command: ‘cat’, ttyEnabled: true),
//   containerTemplate(name: 'gradle', image: 'gradle:4.5.1-jdk9', command: 'cat', ttyEnabled: true),
  containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true),
//   containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl:v1.8.8', command: 'cat', ttyEnabled: true),
//   containerTemplate(name: 'helm', image: 'lachlanevenson/k8s-helm:latest', command: 'cat', ttyEnabled: true),
  containerTemplate(name: 'jnlp', image: 'jenkinsci/jnlp-slave:latest', args: '${computer.jnlpmac} ${computer.name}')
],
volumes: [
//   hostPathVolume(mountPath: '/home/gradle/.gradle', hostPath: '/tmp/jenkins/.gradle'),
  hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock')
]) {
node (label){

  //Define all variables
  def project = 'my-project'
  def appName = 'my-first-microservice'
  def serviceName = "${appName}-backend"  
  def imageVersion = 'development'
  def namespace = 'development'
//   def imageTag = "gcr.io/${project}/${appName}:${imageVersion}.${env.BUILD_NUMBER}"
  
  //Checkout Code from Git
  checkout scm
  
  //Stage 1 : Build the docker image.
  stage('Build image') {
      sh("docker build -t latest .")
  }
  
  //Stage 2 : Push the image to docker registry
//   stage('Push image to registry') {
//       sh("gcloud docker -- push ${imageTag}")
//   }
  
  //Stage 3 : Deploy Application
//   stage('Deploy Application') {
//        switch (namespace) {
//               //Roll out to Dev Environment
//               case "development":
//                    // Create namespace if it doesn't exist
//                    sh("kubectl get ns ${namespace} || kubectl create ns ${namespace}")
//            //Update the imagetag to the latest version
//                    sh("sed -i.bak 's#gcr.io/${project}/${appName}:${imageVersion}#${imageTag}#' ./k8s/development/*.yaml")
//                    //Create or update resources
//            sh("kubectl --namespace=${namespace} apply -f k8s/development/deployment.yaml")
//                    sh("kubectl --namespace=${namespace} apply -f k8s/development/service.yaml")
//            //Grab the external Ip address of the service
//                    sh("echo http://`kubectl --namespace=${namespace} get service/${feSvcName} --output=json | jq -r '.status.loadBalancer.ingress[0].ip'` > ${feSvcName}")
//                    break
           
//         //Roll out to Dev Environment
//               case "production":
//                    // Create namespace if it doesn't exist
//                    sh("kubectl get ns ${namespace} || kubectl create ns ${namespace}")
//            //Update the imagetag to the latest version
//                    sh("sed -i.bak 's#gcr.io/${project}/${appName}:${imageVersion}#${imageTag}#' ./k8s/production/*.yaml")
//            //Create or update resources
//                    sh("kubectl --namespace=${namespace} apply -f k8s/production/deployment.yaml")
//                    sh("kubectl --namespace=${namespace} apply -f k8s/production/service.yaml")
//            //Grab the external Ip address of the service
//                    sh("echo http://`kubectl --namespace=${namespace} get service/${feSvcName} --output=json | jq -r '.status.loadBalancer.ingress[0].ip'` > ${feSvcName}")
//                    break
       
//               default:
//                    sh("kubectl get ns ${namespace} || kubectl create ns ${namespace}")
//                    sh("sed -i.bak 's#gcr.io/${project}/${appName}:${imageVersion}#${imageTag}#' ./k8s/development/*.yaml")
//                    sh("kubectl --namespace=${namespace} apply -f k8s/development/deployment.yaml")
//                    sh("kubectl --namespace=${namespace} apply -f k8s/development/service.yaml")
//                    sh("echo http://`kubectl --namespace=${namespace} get service/${feSvcName} --output=json | jq -r '.status.loadBalancer.ingress[0].ip'` > ${feSvcName}")
//                    break
//   }

}
}