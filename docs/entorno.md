# Documentación de mi entorno de desarrollo · Práctica 2

**Nombre y apellidos:** Manuel García
**URL de mi repositorio:** https://github.com/ermanolitox08-sudo/entorno-daw-manuel-garcia

> Rellena cada apartado a medida que avanzas. Donde pone «pega aquí», copia el texto
> de la terminal (no hace falta captura). Escribe con tus palabras: no se valora la longitud,
> sino que se note que entiendes lo que has hecho.

---

## 1. Instalación de entornos (CE 2.a)

### 1.1. Entorno vacío (paso 3)

Resultado de `java -version` y `node -v` **antes** de instalar nada:

```
bash: java: command not found
bash: node: command not found
```

¿Por qué crees que aparece ese mensaje? (relaciónalo con la diapositiva «Problemas habituales del entorno»)

> Aparece porque Java y Node.js todavía no están instalados en nuestro entorno de desarrollo, por lo que la terminal no reconoce sus comandos.

### 1.2. Después de la 1.ª reconstrucción (paso 5)

Resultado de `java -version`, `node -v` y `jupyter lab --version` **después**:

```
openjdk version "27" 2026-09-15
OpenJDK Runtime Environment Temurin-27+35 (build 27+35)
OpenJDK 64-Bit Server VM Temurin-27+35 (build 27+35, mixed mode, sharing)

v24.22.1

4.6.4
```

¿Qué líneas nuevas han aparecido en `devcontainer.json`? Explica con tus palabras qué hace cada una:

> Han aparecido las líneas `features`, `java:1`, `node:1` y `python:1`.

- `features`: permite añadir herramientas al entorno.
- `java:1`: instala Java para poder ejecutar programas Java.
- `node:1`: instala Node.js para trabajar con JavaScript y TypeScript.
- `python:1`: instala Python y, con `installJupyterlab: true`, también instala JupyterLab.

### 1.3. Comparativa de los dos IDE (paso 6)

| | Editor de GitHub Codespaces | JupyterLab |
|---|---|---|
| ¿Libre o propietario? | Propietario | Libre y de código abierto |
| Licencia / empresa o comunidad | GitHub, propiedad de Microsoft | Licencia BSD-3-Clause. Lo mantiene Project Jupyter y su comunidad |
| ¿Tiene coste? ¿Con qué límites? | Gratis hasta 120 horas de núcleo y 15 GB-mes en GitHub Free. Con 2 núcleos son 60 horas de uso al mes | Gratuito, sin límite de uso propio |
| ¿Se puede usar fuera de GitHub? | Se accede desde GitHub y se puede conectar con VS Code | Sí, se puede instalar en un ordenador |
| Lo que más me ha gustado | Poder programar desde el navegador sin instalar nada | Poder abrir archivos y usar la terminal fácilmente |
| Lo que menos me ha gustado | Tarda un poco en preparar el entorno | Me costó conectarme al servidor al principio |
| ¿Para qué tipo de trabajo lo elegiría? | Para proyectos de programación en equipo | Para trabajar con Python y cuadernos de datos |

---

## 2. Módulos y extensiones (CE 2.b)


| Extensión | ¿Para qué sirve? | ¿Qué cambió al instalarla? | ¿La mantengo? ¿Por qué? |
|---|---|---|---|
| Extension Pack for Java | Sirve para programar, ejecutar y depurar programas Java. | Aparecieron las opciones Run y Debug y pude ejecutar la factura. | Sí, porque la necesito para trabajar con Java. |
| Code Spell Checker | Sirve para detectar posibles faltas de ortografía en el código. | Empezó a subrayar palabras españolas que no reconocía. | No, porque marcaba como incorrectas palabras que estaban bien escritas en español. |
  

¿Qué diferencia hay entre instalar una extensión **solo desde el panel** y añadirla **también a `devcontainer.json`**?

> Instalar una extensión desde el panel solo la añade al entorno actual. Si también la añadimos a devcontainer.json, queda guardada en la configuración del proyecto y se instalará automáticamente al reconstruir el entorno.

---

## 3. Personalización y automatización (CE 2.c)

- **Tema visual elegido** (paso 10) y por qué: El Oscuro predeterminado, porque ya me he acostumbrado.
- **Ajuste del proyecto** (paso 10). ¿Qué archivo se ha creado y qué contiene? Se ha creado el archivo `.vscode/settings.json`, que guarda la configuración del proyecto para formatear los archivos automáticamente al guardarlos.

```
{
  "editor.formatOnSave": true
}
```

- **Atajo de teclado** (paso 11). ¿Qué acción, qué combinación y para qué te sirve? He configurado un atajo de teclado para reconstruir el contenedor de Codespaces, de manera que puedo hacerlo más rápido sin buscar la opción en los menús. Control + Option + Shift + R
- **Snippet** (paso 12). ¿Qué escribes y qué aparece? Escribo cabecera en Prueba.java y pulso Enter. Aparece automáticamente una cabecera con los datos del archivo y mi nombre, Manuel García.
- **Automatización al crear el entorno** (paso 14). ¿Qué hace `postCreateCommand` y qué archivos/carpetas han aparecido después de reconstruir? postCreateCommand ejecuta automáticamente npm install al crear el entorno. Sirve para instalar las dependencias del proyecto. Después de reconstruir aparecieron la carpeta node_modules y el archivo package-lock.json, que guarda las versiones exactas de las dependencias.
- **Tareas** (paso 13). ¿Cuántas tareas hay en `tasks.json` y qué hace cada una? Hay 3 tareas. La primera compila el programa Java, lo empaqueta en un archivo `.jar` y lo ejecuta. La segunda compila y ejecuta el programa TypeScript con Node.js. La tercera ejecuta las dos tareas anteriores en orden.

¿Qué parte de toda esta configuración es **personal** (solo para ti) y qué parte es **del proyecto** (la recibe cualquiera que abra el repositorio)?

> La configuración personal es la que solo me afecta a mí, como el tema oscuro y el atajo de teclado. La configuración del proyecto se guarda en el repositorio y la puede utilizar todo el equipo, como settings.json, los snippets, las tareas y devcontainer.json.

---

## 4. Ejecutables de diferentes lenguajes en el mismo entorno (CE 2.e)

Salida completa de la tarea **Build completo** (paso 15):

```
=== FACTURA generada con Java 27 ===
Dominio web anual             12.00 EUR
Alojamiento web               59.90 EUR
Logotipo corporativo         150.00 EUR
-------------------------------------
Base imponible               221.90 EUR
IVA (21 %)                    46.60 EUR
TOTAL                        268.50 EUR

=== FACTURA generada con Node.js v24.22.1 ===
Dominio web anual             12.00 EUR
Alojamiento web               59.90 EUR
Logotipo corporativo         150.00 EUR
-------------------------------------
Base imponible               221.90 EUR
IVA (21 %)                    46.60 EUR
TOTAL                        268.50 EUR
```

| Lenguaje | Archivo fuente | Herramienta que lo traduce | Archivo generado | Cómo se ejecuta |
|---|---|---|---|---|
| Java | `src/java/Factura.java` | `javac` | `build/factura.jar` | `java -jar build/factura.jar` |
| TypeScript | `src/ts/factura.ts` | `tsc` | `dist/factura.js` | `node dist/factura.js` |

**Opcional:** ¿has podido ejecutar los mismos archivos desde JupyterLab (paso 19)? ¿Por qué funciona en los dos IDE sin instalar nada más?

> 

---

## 5. Sistema de actualizaciones (CE 2.d)


| Elemento | ¿Quién lo actualiza? | Modo (automático / manual / ninguno) | Qué he configurado yo |
|---|---|---|---|
| El editor de Codespaces | GitHub | Automático | GitHub actualiza el editor, yo no puedo elegir cuándo |
| Las extensiones | Yo | Ninguno (automático desactivado) | He puesto Auto Update en off para evitar cambios durante los exámenes |
| Java | Yo | Manual | He fijado Java 21 LTS en devcontainer.json para evitar que cambie de versión automáticamente al reconstruir.|
| Node.js | La receta del entorno | Automático | Lo dejo con la versión LTS predeterminada, sin fijar una versión |
| Dependencias npm (lodash, typescript...) | Yo | Manual | Las gestiono con package.json y package-lock.json y comprobaré sus vulnerabilidades |
  

Versión de Java **antes** (paso 5) y **después** (paso 18):

```
ANTES (paso 5):
openjdk version "27" 2026-09-15
OpenJDK Runtime Environment Temurin-27+35 (build 27+35)
OpenJDK 64-Bit Server VM Temurin-27+35 (build 27+35, mixed mode, sharing)

DESPUÉS (paso 18):
Pendiente de reconstruir el entorno con Java 21.
openjdk version "21" 2023-09-19 LTS
OpenJDK Runtime Environment Microsoft-8425986 (build 21+35-LTS)
OpenJDK 64-Bit Server VM Microsoft-8425986 (build 21+35-LTS, mixed mode, sharing)
```

Resultado de `npm outdated` (paso 17):

```
Package          Current    Wanted     Latest
@types/lodash     4.14.202  4.14.202   4.17.27
@types/node       20.11.30  20.11.30   26.6.5
lodash             4.17.20   4.17.20    4.18.1
typescript          5.4.5     5.4.5    7.0.2
```

Resultado de `npm audit` **antes** de actualizar lodash (solo el resumen final):

```
1 high severity vulnerability

To address all issues, run:
  npm audit fix --force
```

Resultado de `npm audit` **después**:

```
found 0 vulnerabilities
```

**Mi política de actualizaciones**: si este entorno lo usara un equipo de 5 personas durante todo el curso, ¿qué dejarías en automático y qué fijarías a mano? Justifícalo.

> Dejaría que GitHub actualizara automáticamente el editor de Codespaces y mantendría Node.js en su versión LTS predeterminada. Las extensiones las actualizaría manualmente para evitar problemas durante las clases o los exámenes. También fijaría Java en la versión 21 LTS y revisaría las dependencias npm antes de actualizarlas, comprobando después que todo sigue funcionando. Así los cinco compañeros tendríamos un entorno más estable durante el curso.

---

## 6. Incidencias

Anota cualquier problema que hayas tenido y cómo lo resolviste (también si usaste un fragmento completo).

> Al principio Java y Node.js no estaban instalados, así que los añadí en devcontainer.json y reconstruí el entorno. También tuve problemas para acceder a JupyterLab y lo solucioné utilizando el token de acceso. Además, cambié el atajo de teclado porque la primera combinación no funcionaba. Para configurar el snippet utilicé el archivo proporcionado por el profesor.

## 7. Reflexión final

¿Qué ventaja tiene describir el entorno «como código» frente a instalar cada programa a mano en tu ordenador? Piensa en un equipo con Mac y Windows.

> La ventaja es que todos los compañeros podemos utilizar el mismo entorno de desarrollo, aunque unos tengan Mac y otros Windows. Al estar la configuración guardada en archivos, no tenemos que instalar cada programa manualmente y evitamos problemas por tener distintas versiones. Además, si alguien nuevo entra al proyecto, puede preparar su entorno fácilmente con la misma configuración.
