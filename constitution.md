# Constitución · Mesa de Ayuda

Acuerdos del proyecto. Cambian poco y solo con acuerdo del equipo.

## Misión y audiencia

API de tickets de soporte, con SLA por prioridad y escalamiento en tres niveles. No incluye chat en vivo ni facturación.

La usan soporte y operaciones. El cliente final no accede a la API. Soporte crea cada ticket en nombre del cliente.

## Stack

Python con FastAPI, PostgreSQL como base, pytest y Docker Compose. En los tests, SQLite. Las versiones se fijan al implementar. Los specs de cada fase no deciden stack: el stack vive acá.

## Calidad

Primero el test. Cada criterio `R<n>` del spec tiene al menos un test.

Todo cambio entra por merge request. Operaciones aprueba el comportamiento de negocio. Ingeniería revisa el código.

## Seguridad y datos

Solo datos sintéticos: no se usan datos reales de personas ni de sistemas. Ningún secreto en el repo: la configuración va por variables de entorno.

Un ticket no se borra de la base. El borrado es lógico, lo realiza operaciones, y el registro permanece.

## Forma de trabajo

El orden de trabajo vive en [specs/backlog.md](specs/backlog.md): fases chicas, una historia `MDA-n` por fase. Un spec por fase en `specs/NNN-<slug>/spec.md`, enlazado a su historia.

Si el comportamiento cambia, cambia primero el spec.
