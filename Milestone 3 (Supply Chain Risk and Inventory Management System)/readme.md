**Supply Chain Risk and Inventory Management System - Milestone 3**

**Project Overview**

In this milestone, we've developed an advanced supply chain inventory management system specifically tailored for lithium-ion battery inventory management. The system goes beyond traditional inventory tracking by incorporating sophisticated risk prediction, real-time monitoring, and adaptive management strategies.

**Detailed Functionality Breakdown**

**1\. Risk Prediction (predict_risk)**

**What We Achieved**

The risk prediction function is the cornerstone of our intelligent inventory management system. It combines multiple data sources to generate a comprehensive risk assessment:

- **Input Parameters**:
  - Inventory Levels: Current stock quantity
  - Lead Times: Duration between order and delivery
  - News Sentiment: Extracted from provided JSON articles
  - Textual Risk: Qualitative risk assessment
- **JSON File Integration** Our JSON file plays a crucial role in risk assessment:
  - Contains news articles about battery technology and market trends
  - Includes detailed sentiment analysis for each article
  - Provides a rich, contextual layer to risk calculation

**How It Works**

1. Sentiment Analysis:
    - Uses TextBlob to analyze news article sentiment
    - Converts sentiment from \[-1, 1\] to \[0, 1\] scale
    - More positive sentiment reduces risk factor
2. Normalization:
    - Converts raw input values to comparable \[0, 1\] range
    - Ensures fair comparison across different metrics
3. Weighted Risk Calculation:
    - Dynamically adjusts weights based on sentiment
    - Combines normalized inputs
    - Generates a risk score between 0-1
4. Risk Labeling:
    - High Risk: Score > 0.7
    - Medium Risk: Score 0.3 - 0.7
    - Low Risk: Score < 0.3

**2\. Inventory Management**

**Strategic Approach**

- Adapts inventory levels based on predicted risks
- Implements dynamic stock adjustments
- Maintains risk factor for each product

**Risk Multipliers**

- High Risk: Reduce stock by 50%
- Medium Risk: Reduce stock by 25%
- Low Risk: No stock reduction

**3\. Damage Tracking (log_damage)**

**Purpose**

- Comprehensive recording of stock damage
- Automatic inventory reconciliation
- Detailed damage reason documentation

**Features**

- Timestamps each damage event
- Reduces inventory automatically
- Provides audit trail for quality control

**4\. Transport Delay Monitoring**

**Tracking Mechanism**

- Records expected vs. actual delivery times
- Logs detailed delay reasons
- Helps identify supply chain bottlenecks

**Key Information Captured**

- Product identification
- Expected delivery date
- Actual delivery date
- Specific delay reasons

**5\. Sales Performance Tracking**

**Intelligent Monitoring**

- Compares current sales with historical averages
- Identifies significant sales volume changes
- Generates alerts for unusual sales patterns

**Sales Status Categories**

- Normal Sales: Within expected range
- Reduced Sales: Significant drop in volume

**6\. Data Export Functionality**

**Comprehensive Reporting**

- Generates CSV files for all database tables
- Enables easy data analysis
- Provides transparent, accessible records

**JSON File: The Secret Weapon**

**How the JSON Contributes**

1. **Dynamic Risk Weighting**
    - Sentiment scores from articles adjust risk calculation
    - More positive news reduces perceived risk
2. **Contextual Market Intelligence**
    - Incorporates real-world market trends
    - Provides nuanced risk assessment beyond numeric metrics
3. **Adaptive Configuration**
    - Risk weights dynamically update based on article sentiments
    - Ensures risk model remains current with market conditions

**Example Scenario**

In our sample JSON:

- Articles about battery technology
- Sentiment analysis scores
- Detailed risk assessments

The system uses these to:

- Adjust inventory levels
- Modify risk factors
- Generate intelligent alerts

**Technical Architecture**

**Database Design**

- **Inventory Table**: Stock levels, risk factors
- **Damage Log**: Stock damage records
- **Transport Delays**: Shipping information
- **Sales Log**: Sales performance tracking

**Technological Innovation**

- Machine learning-inspired risk prediction
- Real-time inventory management
- Adaptive stock control
- Comprehensive supply chain visibility

**Potential Future Enhancements**

1. More advanced machine learning models
2. Integration with external supply chain APIs
3. Predictive maintenance algorithms
4. Advanced visualization dashboards

**Technical Requirements**

- Python 3.8+
- Libraries:
  - sqlite3 (Database management)
  - pandas (Data manipulation)
  - matplotlib (Visualization)
  - textblob (Sentiment analysis)