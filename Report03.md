@4723208 ➜ /workspaces/WE-Docker (main) $ docker ps
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS          PORTS                                         NAMES
6796c5ccca01   postgres:15   "docker-entrypoint.s…"   20 minutes ago   Up 20 minutes   5432/tcp                                      we-docker-db-1
08f4b8004d79   fastapi-app   "uvicorn main:app --…"   44 minutes ago   Up 44 minutes   0.0.0.0:8000->8000/tcp, [::]:8000->8000/tcp   my-fastapi-container