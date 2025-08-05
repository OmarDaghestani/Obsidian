# Threat Sources Identification and Taxonomy (NIST SP 800-30)

This section focuses on identifying and categorizing potential threat sources that could initiate adverse threat events.

## Inputs for Identification
*   Credible threat intelligence information (e.g., from government agencies, industry reports).
*   Organizational-specific threat guidance or profiles.
*   Previous risk assessments and incident reports.

## Threat Source Taxonomy
NIST SP 800-30 categorizes threat sources into four main types:

### 1. Adversarial
*   **Definition:** Individuals, groups, or organizations that pose a threat due to malicious intent and capability.
*   **Examples:**
    *   Cyber criminals
    *   Nation-state actors
    *   Insider threats (malicious employees)
    *   Hacktivists
*   **Characteristics for Assessment:**
    *   **Capability:** The resources and expertise to carry out a threat event.
    *   **Intent:** The motivation or desire to cause harm.
    *   **Targeting:** The specific focus or scope of their potential attacks.

### 2. Accidental
*   **Definition:** Non-malicious human errors or omissions.
*   **Examples:**
    *   Unintentional data deletion or modification.
    *   Misconfiguration of systems by administrators.
    *   Accidental disclosure of sensitive information.
*   **Characteristics for Assessment:** Assessed based on the **range of effects** (e.g., how widely an error could propagate).

### 3. Structural
*   **Definition:** Failures or limitations within organizational systems, infrastructure, or processes.
*   **Examples:**
    *   Hardware failures (e.g., server crash, disk corruption).
    *   Software bugs or vulnerabilities.
    *   Network outages due to infrastructure limitations.
    *   Power supply interruptions.
*   **Characteristics for Assessment:** Assessed based on the **range of effects**.

### 4. Environmental
*   **Definition:** Natural events or phenomena that can cause harm.
*   **Examples:**
    *   Natural disasters (e.g., floods, earthquakes, hurricanes, wildfires).
    *   Extreme weather conditions.
*   **Characteristics for Assessment:** Assessed based on the **range of effects**.

## Assessment Scales
*   NIST SP 800-30 provides specific scales for evaluating:
    *   Adversary Capability (e.g., limited, moderate, high, very high)
    *   Adversary Intent (e.g., low, moderate, high, very high)
    *   Adversary Targeting (e.g., broad, specific, highly specific)
    *   Range of Effects (for non-adversarial sources)

## Representative Threat Events
*   Describes various threat events initiated by these sources.
*   Examples:
    *   **Adversarial:** Reconnaissance, malware delivery, exploitation of vulnerabilities (with detailed TTPs).
    *   **Non-adversarial:** Accidental spills of sensitive information, natural disasters affecting operations.
*   An assessment scale for the **relevance of threat events** (e.g., confirmed, expected, anticipated, predicted, possible) is provided.

---
**See Also:**
*   [[4 NIST SP 800-30 Risk Assessment Process]]
*   [[2 Risk Assessment Key Concepts]]
*   [[7 Likelihood and Impact Assessment]]
*   [[6 Vulnerabilities and Predisposing Conditions]]