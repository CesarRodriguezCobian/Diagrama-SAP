```mermaid
---
config:
  layout: elk
---
flowchart TB
    Activities(("Activities")) ---- Customer(("Customer"))
    Customer --- Opportunity(("Opportunity")) & Lead(("Lead"))
    Customer ---- EquipmentCard(("Equipment Card"))
    Lead --- Supplier(("Supplier")) & Opportunity
    Supplier --- PurchaseQuotation(("Purchase Quotation")) & BusinessPartnerMaster(("Business Partner<br>Master"))
    Opportunity --- Pricing(("Pricing"))
    Pricing --- ItemMaster(("Item Master")) & SalesQuotation(("Sales Quotation"))
    SalesQuotation --- SalesOrder(("Sales Order"))
    SalesOrder --- DeliveryNote(("Delivery Note")) & WarehouseManagement(("Warehouse<br>Management"))
    WarehouseManagement --- PurchaseOrder(("Purchase Order")) & ItemMaster
    PurchaseOrder ---- ProductionOrder(("Production Order")) & GoodsReceiptPO(("Goods Receipt PO")) & Sourcing(("Sourcing")) & PurchaseQuotation
    PurchaseQuotation --- PurchaseRequest(("Purchase Request"))
    ItemMaster --- EquipmentCard
    EquipmentCard --- ServiceCall(("Service Call"))
    ServiceCall --- ServiceContract(("Service Contract"))
    ServiceContract --- ServiceBilling(("Service Billing"))
    Sourcing --- ProductionOrder
    Sourcing ---- MaterialRequirementsPlanning(("Material Requirements<br>Planning"))
    MaterialRequirementsPlanning ---> BillOfMaterials(("Bill of Materials"))
    BillOfMaterials --- DemandPlanning(("Demand Planning"))
    ProductionOrder --- DemandPlanning & BackorderReporting(("Backorder<br>Reporting")) & IssueToProduction(("Issue to Production"))
    DemandPlanning --- BackorderReporting
    BackorderReporting --- InventoryAuditReport(("Inventory Audit<br>Report"))
    InventoryAuditReport --- IssueToProduction & AccountBalancesReport(("Account Balances<br>Report"))
    AccountBalancesReport --- ReceiptFromProduction(("Receipt from Production")) & ProductReporting(("Product<br>Reporting"))
    DeliveryNote --- ARInvoice(("AR Invoice")) & GoodsReceiptPO
    GoodsReceiptPO --- IssueToProduction & APInvoice(("AP Invoice"))
    IssueToProduction --- ReceiptFromProduction & JournalEntries(("Journal Entries"))
    JournalEntries --- ReceiptFromProduction & CostAccounting(("Cost Accounting"))
    CostAccounting --- GLAccountDetermination(("G/L Account<br>Determination"))
    GLAccountDetermination --- GeneralLedgerAccounts(("General Ledger<br>Accounts"))
    GeneralLedgerAccounts --- ChartOfAccounts(("Chart of Accounts"))
    ReceiptFromProduction --- APInvoice & ProductReporting
    ProductReporting --- FinancialReporting(("Financial<br>Reporting"))
    FinancialReporting --- Reconciliation(("Reconciliation"))
    Reconciliation --- CashManagement(("Cash Management"))
    CashManagement --- APARIndicator(("AP / AR")) & IncomingPayments(("Incoming<br>Payments"))
    APARIndicator --- ARInvoice
    ARInvoice --- APInvoice & IncomingPayments
    IncomingPayments --- OutgoingPayments(("Outgoing<br>Payments"))
    OutgoingPayments --- APInvoice
