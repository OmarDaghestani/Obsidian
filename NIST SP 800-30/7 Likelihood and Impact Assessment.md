# Likelihood and Impact Assessment (NIST SP 800-30)

Determining the likelihood of threat events occurring and assessing their potential impact are crucial steps in calculating overall risk.

## Likelihood of Threat Event Occurrence
*   **Definition:** The probability or frequency of a threat event actually materializing and causing an adverse impact.
*   **Inputs for Determination:**
    *   Historical data on cyber attacks and incidents (internal and external).
    *   Security assessment reports (highlighting vulnerabilities).
    *   Threat intelligence and guidance specific to organizational levels.
    *   Effectiveness of existing security controls.

### Assessment Scales for Likelihood
NIST SP 800-30 provides scales to categorize likelihood:
*   **Threat Event Initiation (Adversarial):** Assesses the probability that an adversarial [[5 Threat Sources Identification and Taxonomy|threat source]] will initiate a specific threat event. Factors include:
    *   Adversary Capability
    *   Adversary Intent
    *   Adversary Targeting
*   **Threat Event Occurrence (Non-Adversarial):** Assesses the probability that a non-adversarial threat source (accidental, structural, environmental) will cause a threat event.
*   **Overall Likelihood:** This is determined by combining the likelihood of threat initiation/occurrence with the severity of [[6 Vulnerabilities and Predisposing Conditions|vulnerabilities]] and the effectiveness of existing controls.
    *   *Example Scale:* Very High (10) to Very Low (0), or qualitative descriptors (e.g., High, Moderate, Low, Very Low).

## Impact Assessment of Threat Events
*   **Definition:** The magnitude of harm that could result from a threat event successfully exploiting a vulnerability.
*   **Inputs for Determination:**
    *   Organizational guidance on acceptable risk and impact tolerances.
    *   Identification of critical missions, business processes, and assets.
    *   Exemplary impact scenarios (e.g., from industry-specific guidance or historical incidents).

### Categories of Adverse Impacts
Impacts are categorized based on what is affected:
*   **Harm to Operations:**
    *   Disruption of business processes (e.g., financial operations, critical services).
    *   Loss of productivity, efficiency.
    *   Damage to organizational reputation.
*   **Harm to Assets:**
    *   Loss, corruption, or damage to data (confidentiality, integrity, availability).
    *   Damage or destruction of hardware, software, or infrastructure.
*   **Harm to Individuals:**
    *   Privacy violations (e.g., PII breaches).
    *   Harm to safety or health.
    *   Civil liberty impacts.
*   **Harm to Other Organizations:**
    *   Cascading impacts on partners, suppliers, or customers.
*   **Harm to the Nation:**
    *   Impacts on critical infrastructure, national security, or economic stability.

### Assessment Scale for Impact
*   NIST SP 800-30 provides an assessment scale for the impact of threat events, ranging from:
    *   **Very High:** Multiple severe effects, extensive damage, significant disruption, long recovery time.
    *   **Very Low:** Negligible effects, minimal impact, no noticeable disruption.
*   This scale helps organizations evaluate potential consequences systematically.

## Risk Determination
*   **Inputs:** Utilizes the determined likelihood and impact values.
*   **Process:** Combines likelihood and impact, often using risk matrices or calculations, to arrive at an overall risk level (e.g., High, Moderate, Low).
*   **Prioritization:** Informs decisions on which risks require immediate attention and response.
*   Templates for documenting identified impacts are included for organizational use.

---
**See Also:**
*   [[4 NIST SP 800-30 Risk Assessment Process]]
*   [[2 Risk Assessment Key Concepts]]
*   [[5 Threat Sources Identification and Taxonomy]]
*   [[6 Vulnerabilities and Predisposing Conditions]]
*   [[11 Risk Models and Analysis Approaches]]