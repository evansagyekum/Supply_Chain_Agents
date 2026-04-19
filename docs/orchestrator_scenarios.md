# Orchestrator Logic & Event Scenarios

## Core Logic Principles
1. **Safety & Compliance**: Overrides all other priorities.
2. **Supply Continuity**: Secondary priority to ensure no production downtime.
3. **Cost**: Optimization factor considered only when Safety and Continuity are guaranteed.

## Simulated Scenarios

### Scenario 1: The Cascading Inventory Shortage
*   **Event Type**: Inventory Drop
*   **Substance**: Toluene (CAS: 108-88-3)
*   **Decision Priority**: **HIGH**
*   **Action**: Expedite order. Bypass standard SLA to get materials same-day.

### Scenario 2: The E-mail Supplier Delay
*   **Event Type**: Supplier Delay
*   **Substance**: Platinum Catalyst-B
*   **Decision Priority**: **MEDIUM**
*   **Action**: Buy small expensive emergency batch from local spot-market to bridge the 2-day gap.

### Scenario 3: Hazardous Material Compliance Block
*   **Event Type**: Compliance Issue
*   **Substance**: N-Methyl-2-pyrrolidone (NMP)
*   **Decision Priority**: **CRITICAL**
*   **Action**: Immediate "DO NOT PROCURE" lock. Alert EHS Director for disposal/transfer.

### Scenario 4: The Unforeseen Demand Spike
*   **Event Type**: Demand Spike
*   **Product**: Ammonium Nitrate Fertilizer
*   **Decision Priority**: **HIGH**
*   **Action**: Initiate "Just-in-Time" staggered micro-deliveries to stay under storage limits.
