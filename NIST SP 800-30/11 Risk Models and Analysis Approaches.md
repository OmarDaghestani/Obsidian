# Risk Models and Analysis Approaches (NIST SP 800-30)

Risk models define the factors to be assessed and their relationships, guiding the risk assessment process. Organizations can choose from quantitative, qualitative, or semi-quantitative methods based on their needs and culture.

## Risk Models
*   **Purpose:** Provide a structured framework for understanding the dynamics of risk and improving communication about risks.
*   **Components/Factors:**
    *   [[2 Risk Assessment Key Concepts|Threats]]
    *   [[6 Vulnerabilities and Predisposing Conditions|Vulnerabilities]]
    *   [[7 Likelihood and Impact Assessment|Likelihood]]
    *   [[7 Likelihood and Impact Assessment|Impact]]
    *   Predisposing conditions
*   **Flexibility:** Models can vary in detail and complexity, tailored to specific organizational needs, available data, and expertise.
*   **Benefits:**
    *   Enhance reproducibility and repeatability of assessments.
    *   Provide a consistent way to evaluate and compare risks.

## Assessment and Analysis Approaches

### 1. Quantitative Assessments
*   **Method:** Use numerical values for risk factors (e.g., financial cost, probability percentages).
*   **Advantages:**
    *   Provides rigorous, objective analysis.
    *   Allows for precise comparison and prioritization of risks.
    *   Enables calculation of Return on Investment (ROI) for security controls.
*   **Disadvantages:**
    *   Requires significant data (historical, financial) that may be difficult to obtain or unreliable.
    *   Can be resource-intensive and time-consuming.
    *   Results may require careful interpretation by non-technical stakeholders.
    *   Requires specialized expertise.

### 2. Qualitative Assessments
*   **Method:** Categorize risks using descriptive terms (e.g., High, Medium, Low for likelihood and impact).
*   **Advantages:**
    *   Easier and faster to conduct, requiring less specific data.
    *   More accessible and understandable for a wider audience, including non-technical stakeholders.
    *   Useful for initial assessments or when data is scarce.
*   **Disadvantages:**
    *   Lacks precision in prioritization, making it hard to differentiate between similar "medium" risks.
    *   Can be subjective and prone to biases of the assessors.
    *   May not provide sufficient detail for precise resource allocation decisions.

### 3. Semi-Quantitative Assessments
*   **Method:** Combines elements of both quantitative and qualitative approaches. Assigns numerical scales to qualitative categories (e.g., Likelihood High = 7, Medium = 4, Low = 1).
*   **Advantages:**
    *   Offers a balance between rigor and ease of implementation.
    *   Provides more precision than purely qualitative methods for prioritization.
    *   Better for communication than pure quantitative results for many audiences.
    *   Reduces subjectivity compared to pure qualitative.
*   **Disadvantages:**
    *   The assignment of numerical values to qualitative terms can still be somewhat arbitrary.
    *   May be misinterpreted as more precise than they actually are.

## Analysis Approaches (Focus/Perspective)
The chosen analysis approach determines the starting point and primary focus of the risk assessment:

*   **Threat-Oriented:** Starts by identifying [[5 Threat Sources Identification and Taxonomy|threat sources]] and [[5 Threat Sources Identification and Taxonomy|threat events]], then explores how they could exploit vulnerabilities and cause impact.
*   **Asset/Impact-Oriented:** Begins by identifying critical assets or potential adverse impacts (e.g., mission disruption, data loss), then works backward to identify the threats and vulnerabilities that could lead to those impacts.
*   **Vulnerability-Oriented:** Focuses on identifying [[6 Vulnerabilities and Predisposing Conditions|vulnerabilities]] within systems or processes, then determines what threats could exploit them and what impacts might result.

## Organizational Culture's Impact
*   Organizational culture significantly influences the choice of risk models and assessment approaches.
*   Different cultural attitudes towards risk (e.g., risk-averse vs. risk-tolerant) can predispose an organization to favor certain methods.
*   Risk frames (how risk is conceptualized and communicated) establish the foundation for managing risk and guiding decisions.
*   Effective communication of risks is essential regardless of the approach chosen.

---
**See Also:**
*   [[4 NIST SP 800-30 Risk Assessment Process]]
*   [[2 Risk Assessment Key Concepts]]
*   [[7 Likelihood and Impact Assessment]]
*   [[8 Risk Assessment Reports and Communication]]