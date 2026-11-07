# Entrega_1_IYEC
Entregable 1 del curso de Integración y Entrega Continua, Especialización en Desarrollo de Software, EAFIT.

## Integrantes

- JOHN EMMANUEL CORREA CORREA — usuario de GitHub: `imKorr` (propietario del repositorio)

## Ejecución exitosa del workflow

[Ver ejecución de mi_workflow.yml](https://github.com/imKorr/Entrega_1_IYEC/actions/runs/42381354640)

## Preguntas

### 1. ¿Qué eventos configuraste para disparar tu workflow y por qué?

Configuré el evento `push` para que el workflow se active cada vez que hago un commit y lo subo a la rama `main`. También habilité `workflow_dispatch`, que permite ejecutarlo manualmente desde la web de GitHub sin necesidad de enviar commits.

### 2. ¿Qué sistema operativo utiliza el runner `ubuntu-latest` y por qué puede ejecutar tu workflow aunque tu computadora sea Windows o macOS? ¿Qué relación tiene el runner con el shell de los pasos `run`?

El runner `ubuntu-latest` usa Linux (Ubuntu). Los comandos no se ejecutan en mi computadora, sino en una máquina de GitHub que ofrece cómputo gratuito; por eso no importa si yo uso Windows o macOS. Como escogí un servidor Ubuntu, los pasos `run` se ejecutan en el shell bash de Linux, y por eso puedo usar comandos como `echo` y `date`. Es decir, el sistema operativo del runner define qué shell y qué comandos se pueden usar en los pasos `run`.

### 3. Menciona al menos 3 acciones pre-construidas del Marketplace de GitHub Actions no mencionadas en este material. Describe qué hacen y para qué sirven.

1. **`actions/setup-node`:** instala Node.js en el runner. Sirve para proyectos JavaScript/TypeScript.
2. **`docker/build-push-action`:** construye una imagen Docker y la sube a un registro. Sirve para empaquetar y desplegar aplicaciones.
3. **`actions/cache`:** guarda archivos entre ejecuciones, por ejemplo las librerías que instala `pip` en un proyecto con FastAPI. Sirve para no descargarlas cada vez y que el workflow sea más rápido.

### 4. ¿Qué es un secreto en GitHub Actions y para qué se usa? ¿Cómo lo usarías en tu workflow?

Un secreto es una API key o una credencial de seguridad, como una llave privada. En GitHub Actions los secretos se guardan cifrados en la configuración del repositorio, así no quedan escritos en el código ni corren el riesgo de aparecer publicados. En el workflow los usaría como variables de entorno (con `${{ secrets.NOMBRE }}`) para conectar mis scripts con sistemas externos y consultarlos.

### 5. Reflexiona sobre el uso de GitHub Actions en tu flujo de trabajo diario. ¿Qué tareas automatizarías? ¿Por qué?

**JOHN EMMANUEL CORREA CORREA:**

- Automatizaría las consultas al ERP de la empresa y la generación de reportes, para no tener que mantener prendido el PC de la empresa con Claude, que a veces cierra la sesión y no ejecuta los workflows. Usaría un `schedule` a las 8 a. m. todos los días; como Odoo está en la web y tiene workers, está disponible todo el tiempo.

- Conectaría tareas que extraigan información de mi correo y se la envíen a la API de Claude, para tener ese proceso funcionando todo el tiempo sin tener que prender Claude.
