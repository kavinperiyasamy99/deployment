import groovy.json.JsonOutput

node{
  stage('Checkout') {
    checkout scm
    sh "echo In checkout"
  }  
  if( params.version == 'LATEST'){
      return;
  }
  stage('Deployment'){
      sh "echo in deployment"
      deployApp("${params.application}","${params.version}")
  }
}

def deployApp(app_name, tag){
    echo "In deployApp Method"
    switch (app_name) {
        
        case "docker-example":
            echo "Deploying docker-example"
            deployJob("${app_name}", "${tag}","docker-example-job")
            break
        default:
            echo "No app found ${app_name} to deploy"
            break
    }   
}

def deployService(app_name,tag)
{    
    echo "Deploying Service ${app_name}"
       status = 0
    if ( status == 0 ) {
      echo "${app_name} deployed successfully"
      } else {
      echo "${app_name} deployment failed"
      sh "exit 2"
      }
}





