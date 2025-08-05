# Vulnerabilities and Predisposing Conditions (NIST SP 800-30)

This section focuses on identifying weaknesses (vulnerabilities) and factors (predisposing conditions) that increase the likelihood or impact of a successful threat exploitation.

## Inputs for Identification
*   Credible vulnerability information (e.g., vulnerability databases like CVE, NVD).
*   Organizational-specific vulnerability guidance.
*   Security assessment reports (e.g., penetration tests, vulnerability scans, audit findings).
*   System security plans and architecture documentation.

## Vulnerability Definition
*   A weakness in an information system, security procedures, internal controls, or implementation that could be exploited by a [[5 Threat Sources Identification and Taxonomy|threat source]].

## Predisposing Conditions Taxonomy
Predisposing conditions are factors that affect the likelihood of successful threat exploitation or the magnitude of adverse impact. They are categorized into:

### 1. Information-Related Conditions
*   Pertain to the information itself, its handling, or its sensitivity.
*   **Examples:**
    *   Lack of data classification.
    *   Excessive data retention.
    *   Absence of data encryption for sensitive data.
    *   Weak privacy policies.

### 2. Technical Conditions
*   Relate to weaknesses in hardware, software, or network components.
*   **Examples:**
    *   Unpatched software.
    *   Misconfigured systems or network devices.
    *   Weak authentication mechanisms (e.g., default passwords, no multi-factor authentication).
    *   Open network ports.
    *   Lack of intrusion detection/prevention systems.

### 3. Operational/Environmental Conditions
*   Encompass weaknesses in processes, procedures, physical security, or the operational environment.
*   **Examples:**
    *   Inadequate physical access controls.
    *   Lack of employee security training.
    *   Insufficient incident response plan.
    *   Poor change management procedures.
    *   Over-reliance on a single vendor or technology.
    *   Absence of disaster recovery plans.

## Assessment Scale for Vulnerability Severity
*   NIST SP 800-30 provides an assessment scale (e.g., from Very High (10) to Very Low (0)) to categorize vulnerability severity.
*   This assessment is based on the ease of **exposure** (how easily the vulnerability can be discovered and exploited) and the **potential impact** if exploited.

## Documentation
*   Templates are provided for documenting identified vulnerabilities and predisposing conditions for organizational use. This ensures consistency and thoroughness.

---
**See Also:**
*   [[4 NIST SP 800-30 Risk Assessment Process]]
*   [[2 Risk Assessment Key Concepts]]
*   [[7 Likelihood and Impact Assessment]]
*   [[5 Threat Sources Identification and Taxonomy]]