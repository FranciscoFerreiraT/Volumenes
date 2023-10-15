# Volumenes
## Pasos

### Paso 1: Descargar la imagen 'httpd' y comprobar su disponibilidad

```bash
docker pull httpd:2.4
docker images
Este comando descargará la imagen 'httpd' con el tag 2.4 y verificará si existe en el sistema
```
### Paso 2: Crea el contenedor 'dam_web1' y permite el acceso desde el navegador.
```bash
docker run -d --name dam_web1 -p 80:80 httpd:2.4
Este comando creará un contenedor llamado 'dam_web1', abrirá el puerto 80 en el contenedor y permitirá el acceso desde el navegador.
```
### Paso 3: Monta un directorio local en el contenedor para el directorio 'htdocs' del servidor Apache.
```bash
docker run -d --name dam_web1 -p 80:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd:2.4
Esto montará el directorio 'htdocs' del contenedor en un directorio local de tu elección.
```
### Paso 4: Crea un archivo HTML 'index.html' en el directorio local y verifica el acceso desde el navegador.
### Paso 5: Crea el contenedor 'dam_web2' con el mismo volumen y en otro puerto.
```bash
docker run -d --name dam_web2 -p 9080:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd:2.4
Esto creará un segundo contenedor 'dam_web2' en el puerto 9080, utilizando el mismo volumen que 'dam_web1'.
```
### Paso 6: Comprueba que ambos servidores sirven la misma página.
Abrimos estos enlaces en el navegador

http://localhost:80 (dam_web1)
http://localhost:9080 (dam_web2)
Ambos servidores deberían mostrar la misma página 'index.html'.

### Paso 7: Realiza modificaciones en la página 'index.html' y comprueba que los dos servidores siguen sirviendo la misma página actualizada.
