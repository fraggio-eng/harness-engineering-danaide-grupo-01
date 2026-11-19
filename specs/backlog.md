# Backlog · Mesa de Ayuda

Fases chicas, en orden de implementación. Una historia por fase. El número de Jira no es el orden de trabajo: el orden es esta lista. Se revisa entre fase y fase.

La fase en curso es la primera casilla sin marcar.

- [ ] 1 · [MDA-1](../README.md#historias-cargadas-en-jira) Crear y consultar tickets → [spec](001-tickets/spec.md)
- [ ] 2 · [MDA-2](../README.md#historias-cargadas-en-jira) Asignar y responder tickets
- [ ] 3 · [MDA-3](../README.md#historias-cargadas-en-jira) Cerrar tickets
- [ ] 4 · [MDA-4](../README.md#historias-cargadas-en-jira) SLA por prioridad: vencimientos de primera respuesta y de resolución
- [ ] 5 · [MDA-5](../README.md#historias-cargadas-en-jira) Escalar de nivel (1, 2 y 3)
- [ ] 6 · [MDA-6](../README.md#historias-cargadas-en-jira) SLA vencido: marcar el ticket y escalarlo
- [ ] 7 · [MDA-7](../README.md#historias-cargadas-en-jira) Reportes para operaciones: abiertos por nivel y cumplimiento de SLA

## Decisiones que viajan con las fases

Estados de un ticket: Abierto, En proceso, Derivado, Bloqueado y Cerrado.

- **MDA-1.** Al crear, el ticket exige cliente, título, categoría, prioridad y descripción. El estado inicial es Abierto. Consultar muestra título, descripción, fecha de creación, prioridad, asignación y estado. La asignación puede venir vacía hasta MDA-2. El vencimiento de SLA no se calcula en esta fase.
- **MDA-2.** Asignar y responder. El estado En proceso entra en esta fase.
- **MDA-3.** Cerrar. El estado Cerrado entra en esta fase.
- **MDA-4.** El reloj arranca en la fecha de carga. Los plazos de resolución están en horas hábiles.
  - Primera respuesta: el sistema calcula el vencimiento al crear el ticket. Vence a los 10 minutos.
  - Resolución: Crítica, 24 horas hábiles. Alta, entre 48 y 72 horas hábiles. Media, entre 3 y 5 días hábiles. Baja, entre 1 y 3 semanas hábiles. Alta, media y baja todavía tienen rango: cada una necesita un único valor antes de escribir su spec, si no el criterio no se puede testear.
- **MDA-5.** Escalar de nivel (1, 2 y 3). El estado Derivado entra en esta fase.
- **Bloqueado** es un estado válido y todavía no tiene fase.
