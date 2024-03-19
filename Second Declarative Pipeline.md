## Setup Declarative Pipeline for nodo-app
 Go to your Jenkins dashboard.

🔘 Click on "New Item" to create a new job.

🔘 Enter a name for your job (e.g., "Node-app-ci/cd") and select "Pipeline".

🔘 Click "OK" to create the job.

🔘 Enter the description (e.g., "This is a node-app ci/cd pipeline")

🔘 Tick on Github project and in project url paste the below link:
```bash
https://github.com/CloudOpsRahul/node-todo-cicd.git
```
🔘 In Build Triggers section tick on 
GitHub hook trigger for GITScm polling <br>

🔘 Now in Pipeline section, write pipeline script:
```bash
pipeline {
    agent any
    stages{
    stage("CODE"){
        steps{
            git url : "https://github.com/CloudOpsRahul/node-todo-cicd.git" , branch: "master"
            echo "CODE CLONE SUCCESSFULLY"
        }
    }
    stage("BUILD"){
         steps{
             sh "docker build -t node-app:latest ."
                        echo "CODE BUILD SUCCESSFULLY"
        }
    }
    stage("TEST"){
         steps{
                        echo "CODE TEST SUCCESSFULLY"
        }
    }
    stage("PUSH TO PRIVATE DOCKER HUB REPO"){
         steps{
                        echo "DOcker image push SUCCESSFULLY"
        }
    }
    stage("SONAR"){
         steps{
                        echo "CODE BUILD SUCCESSFULLY"
        }
    }
    stage("OWASP"){
         steps{
                        echo "CODE BUILD SUCCESSFULLY"
        }
    }
    stage("TRIVY"){
         steps{
                        echo "CODE BUILD SUCCESSFULLY"
        }
    }
    stage("DEPLOY"){
         steps{
                        echo "APP DEPLOYED SUCCESSFULLY"
        }
    }
    }
}
```
🔘 Click on Save button.

🔘 Click on Build Now option.
