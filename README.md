# CI-configuration
In this task, you need to set up a local Gitlab instance and use it to build
a CI for the project.
You should use docker executors for this task.
Your CI should contain at least three stages:
- build
- test
- package or deploy
The suggested project to build CI for is Godot engine. However, you can
choose any project you want while it is complicated enough.

Create new network: docker network create gitlab-intranet
Add new record to hosts file: 127.0.0.1 gitlab.local
Then start services with following command: docker-compose up -d
Go to http://gitlab.local.
Clone https://github.com/godotengine/godot.git. 
Create .gitlab-ci.ymlfile in the root of the project.
Set maximum artifact size in an Admin Area.
Register GitLab Runner using following command:
docker-compose exec gitlab-runner 
gitlab-runner register 
--non-interactive 
--url http://gitlab.local 
--registration-token "REGISTRATION_TOKEN_FROM_SETTINGS" 
--name godot-runner 
--executor docker 
--docker-image ubuntu:20 
--docker-network-mode gitlab-intranet
