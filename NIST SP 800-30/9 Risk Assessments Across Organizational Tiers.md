# Risk Assessments Across Organizational Tiers (NIST SP 800-30)

NIST SP 800-30 emphasizes that risk assessments should be conducted at multiple organizational levels, or "tiers," to provide a holistic view of an organization's risk posture. Results from lower tiers inform and feed into higher-tier assessments and decision-making.

## Three Tiers of Risk Management

### Tier 1: Organization Level (Strategic)
*   **Focus:** Managing organizational risk from a strategic, enterprise-wide perspective.
*   **Scope:** The entire organization, its mission, business functions, governance, and overall risk tolerance.
*   **Key Activities:**
    *   Establishing the overall risk management strategy and policy.
    *   Defining organizational risk tolerance and acceptance criteria.
    *   Allocating resources for security across the enterprise.
    *   Making high-level, strategic decisions that affect all lower tiers.
    *   Developing enterprise-wide security architectures.
*   **Outputs:** Inform organizational security policies, strategic planning, and enterprise architecture.
*   **Relationship:** Provides the top-down context and constraints for Tier 2 and Tier 3 assessments.

### Tier 2: Mission/Business Process Level (Tactical)
*   **Focus:** Assessing risks to specific mission or business processes that support the organization's strategic goals.
*   **Scope:** Individual lines of business, departments, or critical functions (e.g., HR, Finance, specific product development).
*   **Key Activities:**
    *   Identifying critical assets and information supporting the process.
    *   Assessing risks to the confidentiality, integrity, and availability of information processed by the mission/business function.
    *   Developing security requirements and controls specific to the process needs.
    *   Making tactical decisions regarding process-level security.
*   **Outputs:** Inform process-specific security plans, control selections, and operational procedures.
*   **Relationship:** Receives guidance from Tier 1 and provides risk information to Tier 1, while providing context for Tier 3 system-level assessments.

### Tier 3: Information System Level (Operational)
*   **Focus:** Assessing risks to specific information systems that support mission/business processes.
*   **Scope:** Individual applications, databases, networks, or computing platforms.
*   **Key Activities:**
    *   Identifying system-specific [[5 Threat Sources Identification and Taxonomy|threats]] and [[6 Vulnerabilities and Predisposing Conditions|vulnerabilities]].
    *   Determining the [[7 Likelihood and Impact Assessment|likelihood]] and [[7 Likelihood and Impact Assessment|impact]] of system-specific threat events.
    *   Selecting and implementing specific security controls for the system ([[NIST SP 800-53]]).
    *   Monitoring the operational effectiveness of system controls.
*   **Outputs:** Inform system security plans, security control implementation, and detailed security assessments.
*   **Relationship:** Receives requirements from Tier 2 and provides detailed risk data and control effectiveness information to Tier 2.

## Interconnectedness of Tiers
*   **Top-Down Guidance:** Tier 1 provides overall direction; Tier 2 translates that into process-specific requirements; Tier 3 implements it at the system level.
*   **Bottom-Up Feedback:** Risk assessment results, control effectiveness data, and new threat/vulnerability information from Tier 3 inform Tier 2. Tier 2 then aggregates and provides input to Tier 1, contributing to the overall organizational risk posture.
*   **Holistic View:** This layered approach ensures that risk management is consistent, comprehensive, and supports decision-making at all levels of the organization.

---
**See Also:**
*   [[1 NIST SP 800-30 Overview]]
*   [[3 Risk Management Process Overview]]
*   [[4 NIST SP 800-30 Risk Assessment Process]]