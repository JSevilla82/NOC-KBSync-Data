# NOC KB Sync - Data Repository

Repositorio centralizado de datos para la herramienta **NOC KB Sync**.

Este repositorio contiene exclusivamente el archivo maestro `Boletin_KBs.json`. Su propósito principal es desacoplar la base de datos mensual de boletines del código fuente de la aplicación de escritorio.

## ¿Por qué un repositorio separado?

La herramienta **NOC KB Sync** está programada para conectarse al inicio y leer automáticamente el archivo `.json` expuesto en este repositorio. Esto aporta las siguientes ventajas operativas:
- **Actualizaciones Silenciosas:** No es necesario recompilar ni reinstalar la herramienta principal en los servidores cada vez que Microsoft libera nuevos boletines mensuales.
- **Sincronización en Tiempo Real:** En el momento en que se edita el JSON en este repositorio (y se hace *commit* a la rama `main`), todos los clientes de la herramienta comenzarán a utilizar el nuevo boletín la próxima vez que se abran.
- **Historial de Boletines:** Se mantiene un control de versiones de todos los cambios de los KBs a lo largo de los meses usando Git.

## Estructura del Archivo

El archivo `Boletin_KBs.json` define los detalles del mes actual y el mapeo de servidores con sus actualizaciones correspondientes:
- **`BulletinMonth` y `BulletinYear`**: Identifican el periodo del parcheo.
- **`Servers`**: Arreglo que vincula nombres o versiones de sistema operativo con los objetos `UpdateID`.
- **`Updates`**: Arreglo maestro con todos los KBs (Número de KB, Tipo, Reinicio Requerido, etc.).

## Modo de Uso

Para actualizar el boletín del mes en curso:
1. Edita el archivo `Boletin_KBs.json` directamente en GitHub o en tu clon local.
2. Añade, elimina o modifica los KBs dentro del arreglo `Updates` y ajusta el `Servers` mapping.
3. Haz un *commit* y *push* de tus cambios. ¡Eso es todo!
