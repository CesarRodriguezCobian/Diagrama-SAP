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

    Inicio(["🏁 Inicio"]):::iniciofin
    Inicio --> SO[("Pedido de Venta<br/>Sales Order")]:::documento
    SO --> TipoEntrega{{"Tipo de entrega"}}:::decision
    TipoEntrega -->|Completa| EntregaTotal[("Entrega Completa<br/>Delivery")]:::documento
    TipoEntrega -->|Parcial| EntregaParcial[("Entrega Parcial<br/>Delivery")]:::documento
    EntregaTotal --> FacturaTotal[["Factura Cliente<br/>A/R Invoice"]]:::documento
    EntregaParcial --> FacturaParcial[["Factura Cliente<br/>A/R Invoice"]]:::documento
    FacturaTotal --> PagoTotal[/"Pago Recibido<br/>Incoming Payment"/]:::pago
    FacturaParcial --> PagoParcial[/"Pago Recibido<br/>Incoming Payment"/]:::pago
    PagoTotal --> Fin(["🏆 Pedido Completado"]):::iniciofin
    PagoParcial --> Pendiente{{"¿Artículos pendientes<br/>por entregar?"}}:::decision
    Pendiente -->|Sí| EntregaParcial
    Pendiente -->|No| Fin
