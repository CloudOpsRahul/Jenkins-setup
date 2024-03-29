## Set up a Freestyle project
 Go to your Jenkins dashboard.

🔘 Click on "New Item" to create a new job.

🔘 Enter a name for your job (e.g., "Django todo app") and select "Freestyle project".

🔘 Click "OK" to create the job.

🔘 Enter the description (e.g., "This is a django todo app")

🔘 Tick on Github project and in project url paste the below link:
```bash
https://github.com/CloudOpsRahul/django-notes-app.git
```
🔘 In Source code management section select Git option 
Paste the url:
```bash
https://github.com/CloudOpsRahul/django-notes-app.git
```
In Branch Specifier (blank for 'any') write main branch

🔘 In Build Triggers section tick on 
GitHub hook trigger for GITScm polling <br>

🔘 In Build Steps select Execute shell option and write the below freestyle pipeline.
```bash
echo "**********CI/CD PIPELINE*************"
echo "build docker image from Dockerfile"
docker built -t django-todo-image:latest .
echo "build using docker compose"
docker-compose up -d
echo "code build done using docker"
```

🔘 Click on Save button.

🔘 Click on Build Now. And check build history, open the particular build history in console output

🔘 Check the console successfully done





