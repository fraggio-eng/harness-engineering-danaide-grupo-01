# MDA-1 — Crear y consultar tickets

Historia: [MDA-1](../../README.md#historias-cargadas-en-jira).

Este spec describe comportamiento. No elige stack, tablas ni endpoints. Esos acuerdos están en [constitution.md](../../constitution.md). El orden de las fases está en [specs/backlog.md](../backlog.md).

## Contexto

Soporte registra un pedido de ayuda en nombre del cliente. El cliente final no usa la API. Soporte y operaciones necesitan crear ese ticket y volver a verlo.

Al crearlo, el ticket lleva cliente, título, categoría, prioridad y descripción. La prioridad es Crítica, Alta, Media o Baja. El estado inicial es Abierto, la asignación queda vacía y en esta fase no se calcula ningún vencimiento de SLA.

## Historias

- Como persona de soporte, quiero crear un ticket en nombre del cliente, para dejar registrado el pedido.
- Como persona de soporte u operaciones, quiero consultar un ticket por su identificador, para ver los datos con los que se creó.
- Como persona de soporte u operaciones, quiero listar los tickets, para ver los pedidos registrados.

## Criterios

- **R1.** SI falta cliente, título, categoría, prioridad o descripción, o alguno queda vacío después de recortar espacios, ENTONCES el sistema DEBE rechazar la creación y no guardar el ticket.
- **R2.** SI la prioridad no es Crítica, Alta, Media ni Baja, ENTONCES el sistema DEBE rechazar la creación y no guardar el ticket.
- **R3.** CUANDO se crea un ticket válido, el sistema DEBE guardarlo y devolver cliente, título, categoría, prioridad y descripción tal como se enviaron.
- **R4.** CUANDO se crea un ticket, el sistema DEBE asignarle un identificador único, estado Abierto, fecha de creación y asignación vacía.
- **R5.** CUANDO se crea un ticket, el sistema DEBE guardarlo sin vencimiento de SLA.
- **R6.** DONDE dos creaciones traen los mismos datos, el sistema DEBE guardar dos tickets distintos.
- **R7.** CUANDO se consulta un identificador que corresponde a un ticket, el sistema DEBE devolver ese ticket con cliente, título, categoría, descripción, fecha de creación, prioridad, asignación y estado.
- **R8.** SI el identificador consultado no corresponde a ningún ticket, ENTONCES el sistema DEBE indicar que no existe.
- **R9.** CUANDO se listan los tickets sin filtros, el sistema DEBE devolverlos ordenados por prioridad (Crítica, Alta, Media, Baja) y, dentro de la misma prioridad, del más antiguo al más reciente, cada uno con título, descripción, fecha de creación, prioridad, asignación y estado.

## Fuera de alcance

- Asignar, responder y pasar a En proceso (MDA-2).
- Cerrar y pasar a Cerrado (MDA-3).
- Calcular SLA de primera respuesta o de resolución, y marcar un SLA vencido (MDA-4, MDA-6).
- Escalar de nivel y pasar a Derivado (MDA-5).
- Reportes para operaciones (MDA-7).
- Borrado lógico, estado Bloqueado, chat en vivo, facturación y acceso del cliente final.
- Autenticación, filtros del listado, paginación y edición de un ticket ya creado.

## Preguntas abiertas

Ninguna. Los filtros del listado quedan para MDA-2. El SLA de resolución quedó en horas, en el setlist, para el spec de MDA-4. Bloqueado sigue anotado hasta que aparezca una historia.
