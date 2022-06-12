# Agregar un HTML personalizado a en servidor web dockerizado Nginx

## Hecho por Joan Pérez Susidko


### Primer paso:

Realizar un pull de nginx en docker con el comando:

```
docker pull nginx
```

![image](https://user-images.githubusercontent.com/101748401/173240333-de6b297d-d591-4d65-b737-d571ec3e9142.png)

### Segundo Paso:

Ejecutamos el contenedor con: 

```
docker run --rm -d -p 8082:80 --name joanperez nginx
```

Uso el puerto 8082 porque tomcat ya está usando 8080.

![image](https://user-images.githubusercontent.com/101748401/173240627-acf57dc9-d639-4baf-80d0-b6431ab22a91.png)

Aquí podemos ver que nginx ya está siendo completamente operativo.

![image](https://user-images.githubusercontent.com/101748401/173240668-229e5b52-1ae9-4031-bd2f-97bcd7e5274b.png)

Lo que sale es una página por defecto de `Nginx`, ahora lo cambiaremos a nuestro gusto.
Lo paramos con:

```
docker stop web
```

### Tercer Paso:

Crearemos una carpeta en documentos donde guardar el `html` que queremos desplegar con el nombre `site-content`.

![image](https://user-images.githubusercontent.com/101748401/173242591-5055704d-290f-4050-91d7-2e3d183e2846.png)

Después de crear el html deseado: 
```
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Docker Nginx</title>
</head>
<body>
  <h2>Hola soy Joan Pérez Susidko</h2>
</body>
</html>
```

Ejecutaremos el siguiente comando para desplegar nuestro `html` personalizado.

```
docker run --rm -d -p 8082:80 --name joanperez -v ~/Documents/nginx/site-content:/usr/share/nginx/html nginx
```

![image](https://user-images.githubusercontent.com/101748401/173244683-9bd55afb-15d9-4bdd-9f0f-3c49a293b454.png)

Y este sería el resultado: 

![image](https://user-images.githubusercontent.com/101748401/173244694-c962ce59-16b1-42fa-8e73-827ae4f5ea93.png)


