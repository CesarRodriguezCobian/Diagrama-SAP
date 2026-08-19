graph LR
    Activities((Activities))
    Customer((Customer))
    Lead((Lead))
    Supplier((Supplier))
    BusinessPartnerMaster((Business Partner<br/>Master))
    
    EquipmentCard((Equipment Card))
    ServiceCall((Service Call))
    ServiceContract((Service Contract))
    ServiceBilling((Service Billing))
    ItemMaster((Item Master))
    WarehouseManagement((Warehouse<br/>Management))
    SalesOrder((Sales Order))
    DeliveryNote((Delivery Note))
    
    Opportunity((Opportunity))
    Pricing((Pricing))
    SalesQuotation((Sales Quotation))
    PurchaseRequest((Purchase Request))
    PurchaseQuotation((Purchase Quotation))
    PurchaseOrder((Purchase Order))
    GoodsReceiptPO((Goods Receipt PO))
    
    ProductionOrder((Production Order))
    IssueToProduction((Issue to Production))
    ReceiptFromProduction((Receipt from Production))
    
    Sourcing((Sourcing))
    MaterialRequirementsPlanning((Material Requirements<br/>Planning))
    DemandPlanning((Demand Planning))
    BackorderReporting((Backorder<br/>Reporting))
    BillOfMaterials((Bill of Materials))
    
    ChartOfAccounts((Chart of Accounts))
    GeneralLedgerAccounts((General Ledger<br/>Accounts))
    GLAccountDetermination((G/L Account<br/>Determination))
    CostAccounting((Cost Accounting))
    InventoryAuditReport((Inventory Audit<br/>Report))
    AccountBalancesReport((Account Balances<br/>Report))
    
    FinancialPostings((Financial<br/>Postings))
    JournalEntries((Journal Entries))
    APInvoice((AP Invoice))
    ARInvoice((AR Invoice))
    APARIndicator((AP / AR))
    CashManagement((Cash Management))
    IncomingPayments((Incoming<br/>Payments))
    OutgoingPayments((Outgoing<br/>Payments))
    Reconciliation((Reconciliation))
    FinancialReporting((Financial<br/>Reporting))
    ProductReporting((Product<br/>Reporting))
    
    Activities --> Customer
    Customer --> Lead
    Lead --> Supplier
    Supplier --> BusinessPartnerMaster
    
    Customer -.-> EquipmentCard
    EquipmentCard -- Service --> ServiceCall
    ServiceCall -- Service --> ServiceContract
    ServiceContract -- Service --> ServiceBilling
    
    EquipmentCard --> ItemMaster
    ItemMaster --> WarehouseManagement
    WarehouseManagement --> SalesOrder
    SalesOrder --> DeliveryNote
    DeliveryNote --> GoodsReceiptPO
    
    Customer --> Opportunity
    Opportunity -- Sales --> Pricing
    Pricing --> SalesQuotation
    SalesQuotation --> SalesOrder
    
    Customer --> PurchaseRequest
    PurchaseRequest -- Purchasing --> PurchaseQuotation
    PurchaseQuotation --> PurchaseOrder
    PurchaseOrder --> GoodsReceiptPO
    
    PurchaseOrder --> ProductionOrder
    ProductionOrder --> IssueToProduction
    IssueToProduction --> ReceiptFromProduction
    
    Sourcing -- Production --> ProductionOrder
    MaterialRequirementsPlanning -- Production --> ProductionOrder
    
    PurchaseRequest -- Sourcing --> Sourcing
    Sourcing --> MaterialRequirementsPlanning
    MaterialRequirementsPlanning --> DemandPlanning
    DemandPlanning --> BackorderReporting
    
    BusinessPartnerMaster --> BillOfMaterials
    BillOfMaterials -.-> ChartOfAccounts
    
    ChartOfAccounts --> GeneralLedgerAccounts
    GeneralLedgerAccounts --> GLAccountDetermination
    GLAccountDetermination --> CostAccounting
    
    DemandPlanning --> CostAccounting
    BackorderReporting --> InventoryAuditReport
    CostAccounting --> InventoryAuditReport
    InventoryAuditReport --> AccountBalancesReport
    
    GoodsReceiptPO --> FinancialPostings
    ProductionOrder -.-> FinancialPostings
    FinancialPostings --> JournalEntries
    JournalEntries --> APARIndicator
    
    SalesOrder --> DeliveryNote
    DeliveryNote --> ARInvoice
    ARInvoice --> APARIndicator
    
    PurchaseOrder --> GoodsReceiptPO
    GoodsReceiptPO --> APInvoice
    APInvoice --> APARIndicator
    
    APARIndicator --> CashManagement
    APARIndicator --> IncomingPayments
    CashManagement --> IncomingPayments
    IncomingPayments --> Reconciliation
    IncomingPayments --> OutgoingPayments
    Reconciliation --> FinancialReporting
    OutgoingPayments --> FinancialReporting
    ReceiptFromProduction --> ProductReporting
    AccountBalancesReport --> ProductReporting
    FinancialReporting --> ProductReporting
