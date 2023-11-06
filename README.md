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

---
1.  Primeiro no docker compose poñeremos a palabra `services`

---
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

---

3. Agora toca a explicación de prestashop, como e parecido ao anterior explicarei as diferenzas.
   - Quitolle o comentario da imagen.
   - Despois poño unha dependencia sobre a base de datos con: `depends_on:` poñendo 
     como opción `- mysql`
   - Agora mapeo os puertos: `ports:` a `8080:80`, sendo o numero da maquina e despois 
     dos dous puntos o porto do contenedor.
   - Na configuración usando `enviroment:` , enlazamos ca base de datos con: `- DB_SERVER: mysql`
    poñemos o nome que se conectara a base de datos `- DB_NAME=prestashop`, tamén o nome do usuario
    que se conectara a base de datos `- DB_USER: root` e para finalizar este apartado poñeremos a contraseña
    a que se conectara a base de datos `- DB_PASSWD: 1234` 
   
---

4. Definimos a network ao ter creados os contenedores.

---
5. E iniciamos os contenedores con: `docker compose up -d` e miramos se nos vai no navegador.

![prestashop_web.png](..%2F..%2FPictures%2FScreenshots%2Fprestashop_web.png)

---
6. Procedemos a intalar o Prestashop.

---
7. Fallo na intalación e aqui quedo esta parte:
![prestashop_fallo.png](..%2F..%2FPictures%2FScreenshots%2Fprestashop_fallo.png)

--- 
8. Creamos a base de datos e rellenamos os datos:

![nuevaBD.png](..%2F..%2FPictures%2FScreenshots%2FnuevaBD.png)

------
![MySQL_creacion.png](..%2F..%2FPictures%2FScreenshots%2FMySQL_creacion.png)

--------
![BD_creada.png](..%2F..%2FPictures%2FScreenshots%2FBD_creada.png)

