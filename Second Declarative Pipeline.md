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

```
🔘 Click on Save button.

🔘 Click on Build Now option.
