# Flazy LEMP (still thinking of a name)
- Nginx
- PHP 7.2-fpm
- MySQL
- Maildev

## :rocket: Quickstart 
- Install and launch Docker  
- `cp .env.dist .env`  
- `docker-compose up`
- Copy Flazy working files in /public
- Install the CMS

| Service      | Path                    |
| ------------ | ----------------------- |
| Website      | `http://localhost:8080` | 
| Mail catcher | `http://localhost:8081` |
| Logs         | `log/`                  |

## :tent: Use a virtual host
- On your machine, run `$ sudo nano /etc/hosts` and add `127.0.0.1   myhost.local`
- Change the server name in `docker/nginx/nginx.conf#L3` to `myhost.local`
- Modify `.env` and set `SERVER_PORT=80`
- Run `$ docker-compose up`
- If it fails make sure no service like Apache is running on port 80 

## About MySQL credentials
If you change mysql credentials in .env you have to re-create mysql container:
- Database will be deleted, make a backup
- Remove container and volume : `$ docker-compose rm -fv mysql`
- Run : `docker-compose up` 
