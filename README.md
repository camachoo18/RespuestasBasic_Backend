## Envío de texto plano

En el backend, puedes usar `res.send()` para enviar una cadena de texto plano.


Se vería algo asi en el back:

```js
app.get('/texto', (req, res) => {
    res.send('Hola mundo, ejemplo ez!');
});
```
Luego con acceder de manera sencilla en la parte de la url con /texto, podrás acceder. En mi caso seria `http://localhost:3000/texto`

## Envío de objeto JSON

Aquí también puedes navegar directamente a la URL y el navegador mostrará el JSON de forma cruda o formateada, dependiendo del navegador
usaremos `res.json`.


Se vería algo asi en el back:

```js
app.get('/json', (req, res) => {
    res.json({ mensaje: 'Hola, mundo!' });
});
```
Navegar a `http://localhost:3000/json` mostrará el JSON directamente en la pestaña del navegador.

## Envío de archivo

Al igual que los anteriores, puedes navegar a la URL y el navegador abrirá el archivo (si es HTML o un formato que puede interpretar)
Para esto usaremos `res.sendFile`.


Se vería algo asi en el back:

```js
const path = require('path');

app.get('/archivo', (req, res) => {
    res.sendFile(path.join(__dirname, 'public', 'gatito.jpg')); 
});

```
Es importante añadir la primera linea para trabajar con rutas de archivos y directorios.
Navegar a `http://localhost:3000/archivo` mostrará el envío de un archivo, en este caso imagen jpg.

## Envio de status especifico.

Aquí, puedes simplemente visitar la URL en el navegador y, si es un error como 404, el navegador te mostrará el mensaje de "No encontrado".
Usaremos el  `res.status`.


Se vería algo asi en el back:

```js
app.get('/error', (req, res) => {
    res.status(404).send('No encontrado');
});
```

Dependiendo del error que muestre, pondra en el navegador un mensaje u otro.
De esta manera podremos asignar un estado a los distintos errores que pueden salir para poder diferenciarlos.
Navegar a `http://localhost:3000/error` mostrará un mensaje similar al siguiente en el navegador

## Redirigir a otra URL

Para las redirecciones, simplemente puedes visitar la ruta inicial y el navegador te redirigirá automáticamente.

Utilizaremos el siguiente `res.redirect`.

Se vería algo asi en el back:

```js
app.get('/redirigir', (req, res) => {
    res.redirect('/otra-ruta');
});

app.get('/otra-ruta', (req, res) => {
    res.send('Has sido redirigido.');
});

```
De esta manera cuando vayas a tu endpoint de `/redirigir`, te llevara a otra ruta y te la mostrará.
Para ello he utilizado la siguiente ruta `http://localhost:3000/redirigir`.

## Enviar HTML
Este caso es muy sencillo, ya que al enviar HTML, el navegador lo renderiza de forma automática

Se vería algo asi en el back:

```js
app.get('/html', (req, res) => {
    res.send('<h1>Has enviado HTML!</h1>');
});

```
De esta manera cuando accedas al endpoint, te mostrará el envio de HTML que hayas hecho, en mi caso un h1
Navegar a `http://localhost:3000/html` mostrará el contenido HTML renderizado, en este caso un título con el texto "Has enviado HTML!" en la página.
