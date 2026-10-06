# Student Task Manager - DevOps Experiment

## Local run
```bash
npm install
npm run dev
```

## Docker
```bash
docker build -t student-task-manager .
docker images
docker run -d -p 3000:80 --name student-task-app student-task-manager
```
Open http://localhost:3000

## GitHub
Create an empty repository, then:
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/student-task-manager.git
git push -u origin main
```

## Jenkins Freestyle
1. Dashboard > New Item > enter `Student-Task-Manager` > Freestyle project > OK.
2. Source Code Management > Git > paste the GitHub repository URL.
3. Branch Specifier: `*/main`.
4. Build Steps > Execute Windows batch command.
5. Paste:
```bat
docker stop student-task-app 2>nul || echo Container not running
docker rm student-task-app 2>nul || echo Container not found
docker build -t student-task-manager .
docker run -d -p 3000:80 --name student-task-app student-task-manager
```
6. Save > Build Now.
7. Console Output should end with `Finished: SUCCESS`.
8. Open http://localhost:3000.

A Jenkinsfile is also included for a Pipeline job.
