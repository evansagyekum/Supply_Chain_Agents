# Dataverse Schema Design for Supply Chain AI

This document outlines the Dataverse schema for the multi-agent supply chain system.

## 1. Suppliers (`sc_supplier`)
*   **Primary Key (GUID)**: `sc_supplierid`
*   **Fields**:
    *   `sc_name` (Primary Name / Single Line of Text)
    *   `sc_tier` (Choice): `Tier 1`, `Tier 2`, `Tier 3`
    *   `sc_contactemail` (Email)
    *   `sc_riskscore` (Decimal, 0.0 - 100.0)
    *   `sc_status` (Choice): `Active`, `Under Review`, `Suspended`

## 2. Inventory (`sc_inventory`)
*   **Primary Key (GUID)**: `sc_inventoryid`
*   **Fields**:
    *   `sc_itemname` (Primary Name / Single Line of Text)
    *   `sc_casnumber` (Single Line of Text)
    *   `sc_currentquantity` (Decimal)
    *   `sc_unit` (Choice): `Liters`, `Kilograms`, `Tons`
    *   `sc_safetystocklevel` (Decimal)
    *   `sc_supplierid` (Lookup to `sc_supplier`)

## 3. ComplianceRecords (`sc_compliancerecord`)
*   **Primary Key (GUID)**: `sc_compliancerecordid`
*   **Fields**:
    *   `sc_name` (Primary Name) 
    *   `sc_inventoryid` (Lookup to `sc_inventory`)
    *   `sc_sds_expirationdate` (Date Only)
    *   `sc_hazardclass` (Choice): `Flammable`, `Toxic`, `Corrosive`, `Oxidizing`
    *   `sc_svhc_flag` (Yes/No)
    *   `sc_maxstoragelimit` (Decimal)

## 4. Orders (`sc_order`)
*   **Primary Key (GUID)**: `sc_orderid`
*   **Fields**:
    *   `sc_ordernumber` (Primary Name / Auto-Numbering)
    *   `sc_supplierid` (Lookup to `sc_supplier`)
    *   `sc_inventoryid` (Lookup to `sc_inventory`)
    *   `sc_quantityordered` (Decimal)
    *   `sc_status` (Choice): `Draft`, `Pending Approval`, `Submitted`, `In Transit`, `Delivered`
    *   `sc_expecteddeliverydate` (Date Only)

## 5. Events (`sc_event`)
*   **Primary Key (GUID)**: `sc_eventid`
*   **Fields**:
    *   `sc_eventcode` (Primary Name / Auto-Numbering)
    *   `sc_eventtype` (Choice): `Inventory Drop`, `Supplier Delay`, `Demand Spike`, `Compliance Alert`
    *   `sc_payload` (Multiple Lines of Text)
    *   `sc_status` (Choice): `New`, `Processing`, `Resolved`, `Failed`
    *   `sc_source` (Single Line of Text)

## 6. Decisions (`sc_decision`)
*   **Primary Key (GUID)**: `sc_decisionid`
*   **Fields**:
    *   `sc_name` (Primary Name / Single Line of Text)
    *   `sc_eventid` (Lookup to `sc_event`)
    *   `sc_prioritylevel` (Choice): `Low`, `Medium`, `High`, `Critical`
    *   `sc_reasoning` (Multiple Lines of Text)
    *   `sc_approvedby` (Lookup to Entra ID/AAD User)

## 7. AgentTasks (`sc_agenttask`)
*   **Primary Key (GUID)**: `sc_agenttaskid`
*   **Fields**:
    *   `sc_taskname` (Primary Name)
    *   `sc_decisionid` (Lookup to `sc_decision`)
    *   `sc_assignedagent` (Choice): `Inventory Agent`, `Supplier Comm Agent`, `Compliance Agent`, `Workflow Agent`
    *   `sc_actionpayload` (Multiple Lines of Text)
    *   `sc_executionstatus` (Choice): `Queued`, `Running`, `Completed`, `Failed`
    *   `sc_resultlog` (Multiple Lines of Text)
