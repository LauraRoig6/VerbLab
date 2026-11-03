# VerbLab · Irregular verbs

Web de práctica con los **88 verbos de las dos fotos**, en el mismo orden y con traducciones al español. Funciona con un solo archivo HTML, sin dependencias, cuentas, claves API ni base de datos.

## Probarla ahora

Abre `index.html` en un navegador. Todo el diseño y el código están dentro del archivo y no necesita descargar fuentes ni recursos externos. Para compartirla con alumnos, publícala siguiendo los pasos siguientes.

## Publicarla con GitHub y Vercel

1. Descomprime este ZIP.
2. Crea un repositorio nuevo en tu GitHub, por ejemplo `verblab`.
3. En **Add file → Upload files**, sube el contenido descomprimido. `index.html` y `vercel.json` deben quedar directamente en la raíz del repositorio, no dentro de una carpeta adicional. Confirma con **Commit changes**.
4. En Vercel, selecciona **Add New → Project** e importa ese repositorio de GitHub. Autoriza el acceso al repositorio si se solicita.
5. Usa estos ajustes si no se aplican automáticamente desde `vercel.json`:

   | Ajuste | Valor |
   | --- | --- |
   | Framework Preset | Other |
   | Root Directory | Raíz del repositorio |
   | Build Command | Vacío, con Override activado para omitir la compilación |
   | Output Directory | `.` |
   | Variables de entorno | Ninguna |

6. Pulsa **Deploy**. Cuando termine, abre la URL de producción que te dé Vercel. Esa es la dirección que puedes compartir con tu alumnado.
7. Las modificaciones que confirmes en la rama de producción de GitHub generarán nuevos despliegues con la integración de Vercel.

El proyecto está preparado para este despliegue; este paquete no implica que ya exista un repositorio o una publicación en tus cuentas.

Documentación oficial consultada el 3 de noviembre de 2026:

- [Configuring a Build — Vercel](https://vercel.com/docs/builds/configure-a-build)
- [Deploying Git Repositories — Vercel](https://vercel.com/docs/git)

## Qué permite

- Seleccionar el primer y el último verbo de un intervalo, ambos incluidos.
- Excluir y recuperar verbos concretos antes de empezar.
- Mostrar **una sola columna** resuelta por fila. El modo aleatorio reparte las pistas entre las cuatro columnas; también se puede fijar una columna.
- Mantener el orden de la lista o mezclar los verbos.
- Completar infinitive, past simple, past participle y translation.
- Corregir la práctica y mostrar los errores junto a las soluciones.
- Ver la nota sobre 10 rodeada en rojo, con estilo de examen.
- Puntuar por verbo completo o por cada casilla.
- Filtrar y repetir únicamente los verbos con errores.
- Recuperar la práctica después de recargar o cerrar la página.
- Consultar la lista y buscar por verbo o traducción.
- Importar otra lista y descargar la lista actual como CSV.
- Imprimir la corrección desde el navegador.

## Puntuación

**Por verbo completo (opción inicial):** una fila suma un punto si todas sus respuestas son correctas. La columna que sirve de pista no cuenta. 15/20 verbos completos dan **7'5** sobre 10.

**Por cada respuesta:** cada casilla a completar vale un punto. Por ejemplo, 43/60 respuestas correctas dan **7'2**. También se indica cuántos verbos completos se han acertado.

La nota se redondea a una cifra decimal. Los errores y los huecos no suman, pero no restan puntos. Si quedan casillas sin responder, se solicita confirmación antes de corregir.

`Can` es modal y no tiene participio: aparece una raya y no se pide ni puntúa esa casilla. Si se elige siempre la pista de participio, en esa fila se muestra el infinitivo.

## Qué respuestas acepta

Se ignoran las mayúsculas y los espacios sobrantes. En español también se ignoran las tildes. Se aceptan las variantes de la lista (p. ej. `burnt` o `burned`) y sinónimos registrados para las traducciones. Es suficiente escribir una variante correcta. Si se escriben varias separadas por `/`, **todas** deben ser válidas.

La lista conserva `got` y `gone / been` tal como aparecen en el libro. La corrección también acepta `gotten` para `get` y otras variantes estándar incluidas en `EXTRA`.

Las pistas españolas distinguen algunos significados próximos: `do` muestra «hacer (una tarea)» y `make` muestra «hacer / fabricar (crear algo)». Las aclaraciones entre paréntesis no son obligatorias al responder. El significado de `lie` es tumbarse, no mentir.

La corrección usa un conjunto de respuestas admitidas; no utiliza IA para interpretar traducciones libres. Si quieres admitir más sinónimos, sepáralos con `/` al importar la lista o añádelos a `EXTRA` dentro de `index.html`.

## Importar una lista propia

En **Lista de verbos → Importar otra lista**, pega una tabla desde Excel o un CSV/TXT. El orden de columnas debe ser:

`infinitive;past simple;past participle;traducción`

Por ejemplo:

```text
be;was / were;been;ser / estar
go;went;gone;ir
eat;ate;eaten;comer
```

Se aceptan tabuladores, punto y coma o comas como separadores. Si una casilla contiene el mismo separador, debe ir entre comillas, como en un CSV estándar. La cabecera es opcional. Máximo 500 verbos, 150 caracteres por casilla y archivo de 300 KB. No se admiten infinitivos repetidos.

La lista importada se guarda **solo en ese navegador**. No cambia la lista que verán otras personas al abrir la web. Para cambiar la lista inicial de todo el alumnado, modifica `RAW` en `index.html` y confirma ese cambio en GitHub. El archivo `lista-del-libro.csv` contiene la lista inicial para facilitar su edición.

## Guardado y alcance

- No hay sincronización entre móviles, ordenadores o distintos navegadores.
- Los datos se guardan localmente en el navegador. Borrar los datos del sitio o cerrar una sesión privada puede eliminarlos.
- El guardado en archivos `file://` puede depender del navegador; el despliegue con URL HTTPS es la opción recomendada para el alumnado.
- No se envían respuestas ni notas a una profesora. Es una herramienta de estudio y autoevaluación.
- Se puede consultar la lista durante una práctica; el resultado lo indica como práctica con consulta.

## Archivos

- `index.html`: aplicación completa.
- `vercel.json`: configuración de Vercel para servir el sitio estático.
- `lista-del-libro.csv`: los 88 verbos en las cuatro columnas.
- `tests/core.test.cjs`: pruebas de corrección, generación de pistas e importación.

Para ejecutar las pruebas con Node.js:

```sh
node tests/core.test.cjs
```

Validación realizada: 12 grupos de comprobaciones del cálculo de nota, variantes, huecos, caso especial de `can`, reparto de pistas, importación y validación de listas. Además se ha probado en navegador el intervalo y la exclusión, el guardado tras recargar, la corrección, el repaso de errores, la importación y la restauración de listas. Diseño revisado en ordenador y en un marco de 390 px para comprobar la adaptación móvil.
