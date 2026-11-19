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

- **MDA-1.** Al crear, el ticket exige cliente, título, categoría, prioridad y descripción. El estado inicial es Abierto. Consultar muestra título, descripción, fecha de creación, prioridad, asignación y estado. El listado no filtra: va por prioridad (Crítica, Alta, Media, Baja) y, dentro de la misma prioridad, del más antiguo al más reciente. La asignación puede venir vacía hasta MDA-2. El vencimiento de SLA no se calcula en esta fase.
- **MDA-2.** Asignar y responder. El estado En proceso entra en esta fase. También entran los filtros del listado por estado, prioridad y cliente.
- **MDA-3.** Cerrar. El estado Cerrado entra en esta fase.
- **MDA-4.** El reloj arranca en la fecha de carga. La primera respuesta vence a los 10 minutos: el sistema calcula ese vencimiento al crear el ticket. La resolución está toda en horas. Se tomó el menor de cada rango anterior para que el criterio sea un solo número y el orden de exigencia se mantenga (1 día = 24 horas, 1 semana = 168 horas).
  - Crítica: 24 horas.
  - Alta: 48 horas.
  - Media: 72 horas.
  - Baja: 168 horas.
- **MDA-5.** Escalar de nivel (1, 2 y 3). El estado Derivado entra en esta fase.
- **Bloqueado** es un estado válido. Queda anotado hasta que aparezca una historia propia. No se agrega a una fase existente.
