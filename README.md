```mermaid
---
config:
  layout: elk
---
flowchart TD
    classDef documento fill:#E3F2FD,stroke:#1565C0,stroke-width:2px,color:#0D47A1;
    classDef decision fill:#FFF3E0,stroke:#EF6C00,stroke-width:2px,color:#E65100;
    classDef pago fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px,color:#1B5E20;
    classDef iniciofin fill:#4A148C,stroke:#12005E,stroke-width:3px,color:#FFFFFF;

    Start(["🏁 Proceso Iniciado"]):::iniciofin
    Start --> Orden[("Orden de Cliente<br/>Sales Order")]:::documento
    Orden --> Modalidad{{"¿Cómo se entregará?"}}:::decision
    Modalidad -->|Todo junto| DespachoCompleto[("Despacho Completo<br/>Delivery")]:::documento
    Modalidad -->|Por partes| DespachoParcial[("Despacho Parcial<br/>Delivery")]:::documento
    DespachoCompleto --> CobroCompleto[["Documento de Cobro<br/>A/R Invoice"]]:::documento
    DespachoParcial --> CobroParcial[["Documento de Cobro<br/>A/R Invoice"]]:::documento
    CobroCompleto --> AbonoCompleto[/"Registro de Abono<br/>Incoming Payment"/]:::pago
    CobroParcial --> AbonoParcial[/"Registro de Abono<br/>Incoming Payment"/]:::pago
    AbonoCompleto --> End(["🏆 Orden Cerrada"]):::iniciofin
    AbonoParcial --> Verificacion{{"¿Quedan unidades sin despachar?"}}:::decision
    Verificacion -->|Sí| DespachoParcial
    Verificacion -->|No| End
