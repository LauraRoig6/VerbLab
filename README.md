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

## Actualizar una web que ya está en GitHub

Sustituye el `index.html` actual de tu repositorio por el de este paquete y confirma el cambio con **Commit changes**. Los demás archivos de la web no necesitan cambios. Si el repositorio ya está conectado a Vercel, la integración publicará el cambio en la rama de producción configurada.

## Puntuación y traducciones

La corrección distingue tres estados: **correcto (verde), parcial (ámbar) e incorrecto (rojo)**.

- Se aceptan los separadores `/` y `-` con o sin espacios: `was/were`, `was / were`, `was-were` y `was - were` equivalen.
- Las variantes inglesas son alternativas: basta `was` o `were`; también basta `burnt` o `burned`.
- Los sinónimos españoles de un mismo significado son intercambiables. Para `begin`, `empezar`, `comenzar` e `iniciar` dan la puntuación completa individualmente.
- Cuando un verbo tiene varios significados, se mantienen todos en la lista para estudiarlos. `be` incluye **ser / estar**; `bite` incluye **morder / picar**. Una sola traducción válida da **el punto completo**, aunque falten otros significados. Debajo aparece una nota informativa con los demás, sin penalización.
- Basta un sinónimo válido de cualquiera de los significados registrados. Por ejemplo, tanto `golpear` como `vencer` son respuestas completas para `beat`.
- Si se mezclan traducciones registradas con otras no válidas, se otorga medio punto y se indica qué parte hay que revisar. Si todas son inválidas o no se responde, la casilla no suma.

**Por verbo (opción inicial):** una fila suma 1 punto si todas sus respuestas son correctas. Si las formas inglesas son correctas y hay una traducción válida, la fila suma el punto completo aunque queden otros significados sin escribir. Solo una mezcla de traducciones válidas e inválidas mantiene el medio punto y el aviso para revisar lo incorrecto. Si hay un fallo en una forma inglesa, la fila no suma en este modo. Ejemplo: `bite / bit / bitten / picar` cuenta como verbo completo, y muestra «También significa: morder» sin descontar puntos.

**Por cada respuesta:** cada casilla a completar vale 1 punto; una traducción parcial vale 0,5. Un verbo con dos formas inglesas correctas y una traducción válida suma **3/3 puntos**, aunque tenga otros significados.

La nota se redondea a una cifra decimal. La pista no se puntúa. Los significados que falten son solo informativos y no envían el verbo al repaso. Los errores y los huecos no restan puntos. Las filas con traducción parcial se incluyen al filtrar o repetir errores e incompletos.

`Can` no tiene participio: la raya no se pide ni se puntúa. Si se fija la pista del participio, en esa fila se muestra el infinitivo.

## Sinónimos y edición de significados

Los 88 verbos tienen grupos de sinónimos revisados en el objeto `MEANINGS` dentro de `index.html`. Cada grupo interior es un significado y sus alternativas. Por ejemplo:

```js
begin: [['empezar', 'comenzar', 'iniciar']],
bite: [['morder', 'dar un mordisco'], ['picar', 'dar una picadura']]
```

Las mayúsculas y los espacios sobrantes no cambian la corrección. En español se ignoran también las tildes. El sistema utiliza sinónimos registrados; no consulta IA ni interpreta cualquier traducción libre. Puedes ampliar `MEANINGS` si necesitas otra traducción válida. En la lista de consulta se pueden ver los sinónimos aceptados y todos los significados para estudiar.

La lista mantiene las formas inglesas de las fotografías. `ENGLISH_EXTRA` añade variantes estándar como `gotten`, `shined` o `showed` como participio.

## Importar una lista propia

En **Lista de verbos → Importar otra lista**, pega una tabla desde Excel o un CSV/TXT. El orden de columnas es:

`infinitive;past simple;past participle;traducción`

Ejemplo:

```text
be;was / were;been;ser + estar
begin;began;begun;empezar / comenzar
bite;bit;bitten;morder + picar
```

Para las traducciones, `/` o `-` separan sinónimos; ` + ` agrupa significados distintos para estudiar, sin exigirlos todos al responder. Para verbos registrados y formas inglesas compatibles, la app reconoce qué significados contiene la lista y acepta sus sinónimos. También reconoce `ser / estar` como dos significados conocidos. No aplica los significados de `lie / lay / lain` a una lista que contenga `lie / lied / lied`.

Para un verbo desconocido, `probar / examinar + comprobar` agrupa dos significados: cualquiera de probar, examinar o comprobar da la puntuación completa; se muestran los demás como nota informativa.

Se admiten tabuladores, punto y coma o comas como separadores de columnas. Si una casilla contiene el mismo separador, debe ir entre comillas. La cabecera es opcional. Máximo 500 verbos, 150 caracteres por casilla y archivo de 300 KB; sin infinitivos repetidos.

La descarga CSV conserva los grupos de sinónimos y significados. La lista importada se guarda solo en ese navegador; no modifica la lista inicial de todo el alumnado. Para cambiar la lista inicial, modifica `RAW` y `MEANINGS` en `index.html` y confirma el cambio en GitHub.

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

Validación realizada: 22 grupos de comprobaciones del cálculo de nota, variantes, huecos, caso especial de `can`, reparto de pistas, importación y validación de listas. Además se ha probado en navegador el intervalo y la exclusión, el guardado tras recargar, la corrección, el repaso de errores, la importación y la restauración de listas. La actualización comprueba además barras y guiones, todos los sinónimos registrados, puntuación completa con una traducción válida en ambos modos, avisos informativos de otros significados, exportación e importación sin pérdida de grupos, repaso de incompletos y visualización móvil de la corrección. Diseño revisado en ordenador y en un marco de 390 px para comprobar la adaptación móvil.
