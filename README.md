# 1º Examen de SXE

---
## PrestaShop

----

Para empezar no compose usaremos un contenedor para a base de datos eu usarei o 
MySQL (dado que a coñezo e tamén xa fixemos probas con postgresSQL e mariaDB), e  outro
contenedor para o PrestaShop. Miramos na páxina web propia de: 
https://devdocs.prestashop-project.org/
<br>
Onde iremos a pagina propia da instalación e ahi copiamos o compose:
https://devdocs.prestashop-project.org/8/basics/installation/environments/docker/

![Docker-compose_Pagina.png](..%2F..%2FPictures%2FScreenshots%2FDocker-compose_Pagina.png)

----
### Creamos e explicamos os contenedores:
1.  Primeiro no docker compose poñeremos a palabra `services`
2. Agora empezamos co contenedor da base de datos:
   - Crease o contenedor da base de datos.
   - Seguimos poñendolle o nome ao servidor do servicio.
   - Cambiamoslle o nombre ao contenedor con: `container_name: mysql`
   - Agora poñemos a imagen do servidor con: `image: mysql:5.7`.
   - Agregamos un `restart: unless-stopped`, e decir que non se para ata que digamos
   - Seguimos cambiando a configuración para poder cambiarlle o nome e a contraseña
     da base de datos. Para cambiar a configuración usamos a palabra `environment:`,
     logo para o nome usamos `- MYSQL_DATABASE=prestashop` e para a contraseña 
    `- MYSQL_ROOT_PASSWORD=1234`
   - Continuamos poñendo a nosa rede propia, personalizada, usando a palabra `networks:`
     e despois poñemoslle o nome `prestashop_network`.


