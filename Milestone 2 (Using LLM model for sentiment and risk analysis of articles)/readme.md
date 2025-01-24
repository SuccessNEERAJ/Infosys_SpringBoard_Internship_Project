## Milestone 2: Advanced News Analysis and Risk Assessment

### Objective
Milestone 2 expanded the project's capabilities by implementing advanced news article analysis specifically focused on Lithium-Ion battery supply chains. The system now incorporates sentiment analysis and sophisticated risk assessment using LLM technology.

### Key Implementations

#### Event Registry API Integration
- Implemented OR operations in keyword search to capture a broader range of relevant articles.
- Keywords include: "Lithium Ion Batteries", "Li-ion Batteries", "Lithium Battery", "EV Batteries".
- Fetches articles from both news and blog sources within a 7-day window.

#### Sentiment Analysis
- Integrated **TextBlob** for robust sentiment analysis of news articles.
- Provides sentiment classification (**POSITIVE**, **NEGATIVE**, **NEUTRAL**).
- Includes confidence scoring for reliability assessment.

#### Risk Analysis with Groq LLaMA
- Implemented structured risk analysis using the LLaMA model.
- Analyzes five key risk categories:
  1. Raw Material Risks
  2. Manufacturing Risks
  3. Geographic Risks
  4. Industry Impact
  5. Mitigation Strategies
- Provides detailed analysis of potential supply chain impacts.

#### Data Processing Pipeline
- Automated article fetching and processing.
- Structured data storage in both DataFrame and JSON formats.
- Real-time analysis logging and result storage.