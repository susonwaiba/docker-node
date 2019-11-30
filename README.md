# Simplest Docker Compose file

```yml
version: "2"
services:
  node:
    image: "node:13.2"
    user: "node"
    working_dir: /home/node/app
#    environment:
#      - NODE_ENV=production
    volumes:
      - ./:/home/node/app
    expose:
      - "8081"
    links:
      - db
    command: "npm start"
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
  db:
    image: "mariadb:10.4"
    ports:
      - 3306
    volumes:
      - ./db_data:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=root
      - MYSQL_DATABASE=database
      - MYSQL_USER=user
      - MYSQL_PASSWORD=pass
      - TERM=meh
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
  redis:
    image: "redis:5.0"
    volumes:
      - ./redis_data:/data
    ports:
      - 6379
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
```


## Updates ?
- Ping me with merge request :D

## Nothing
