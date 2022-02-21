`Nginx-proxy` от jwilder - это прокси-сервер для контейнеров Docker, который ***ВКЛЮЧАЕТ В СЕБЯ*** `docker-gen` для автоматического создания конфигурации для Nginx. Вы можете использовать его для завершения SSL, балансировки нагрузки и т. Д. Но будет трудно управлять nginx-прокси в Kubernetes.

`Nginx-proxy` устанавливает контейнер, в котором работают nginx и docker-gen . `Docker-gen` генерирует конфигурации обратного прокси для nginx и перезагружает nginx при запуске и остановке контейнеров.

Принцип работы `nginx-proxy` довольно простой, он через пробрасываемый сокет докера получает доступ к информации о запущенных контейнерах, анализирует наличие переменной окружения с именем `VIRTUAL_HOST` и перенаправляет запросы с указанного хоста на контейнер, у которого данная переменная окружения задана.

## run jwilder
``` bash
docker network create net
docker-compose up -d --build
```

Ссылки на источники:
1. https://habr.com/ru/post/460173/
2. https://dev.to/adamkdean/automatic-ssl-with-let-s-encrypt-nginx-4nfk
3. https://andreyex.ru/linux/ispolzovanie-docker-dlya-nastrojki-obratnogo-proksi-nginx-s-avtomaticheskoj-generatsiej-ssl/
4. https://techsch.com/tutorials/multiple-websites-jwilder-nginx-proxy-letsencrypt (+ traefik)
5. https://blog.linoproject.net/build-a-secure-connection-with-nginx-container-and-cloudflare/
6. jwilder/nginx-proxy - https://hub.docker.com/r/jwilder/nginx-proxy
7. jwilder/docker-gen - https://github.com/nginx-proxy/docker-gen
