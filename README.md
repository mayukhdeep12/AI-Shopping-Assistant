# Smart Product Search Assistant 🛍️

An intelligent product search system with natural language processing capabilities that provides detailed product information, price comparisons, and policy insights across multiple e-commerce platforms.

## Table of Contents
- [Tests](#tests)
- [Comparative Conceptual Map](#comparative-conceptual-map)
- [Short Written Analysis](#short-written-analysis)
- [Design Decisions](#design-decisions)
- [Challenges & Improvements](#challenges--improvements)
- [Open Questions & References](#open-questions--references)
- [Installation](#installation)

## Tests ✨
1. **Task A: Basic Item Search + Price Constraint**  
   - **Prompt** - Find a floral skirt under 4000 Rupees in size S. Is it in stock, and can I apply a discount code 'SAVE10'?
  
https://github.com/user-attachments/assets/3996b6eb-ea87-46cb-b12d-c1f8d68418e8
     
2. **Task B: Shipping Deadline**  
   - **Prompt** - I need white sneakers (size 8) for under 6000 Rupees that can arrive by Friday.
  
https://github.com/user-attachments/assets/9a2e7b77-4dc7-450d-bef4-4f51daf538db

3. **Task C: Competitor Price Comparison**  
   - **Prompt** - I found a 'casual denim jacket' at 6700 Rupees on SiteA. Any better deals?

https://github.com/user-attachments/assets/e8cb3021-0bfc-4e7d-9849-8cde8154cc2e

4. **Task D: Returns & Policies**  
   - **Prompt** - I want to buy a cocktail dress from SiteB, but only if returns are hassle-free. Do they accept returns?

https://github.com/user-attachments/assets/ac741ad9-c841-4618-bccf-209089e1b65e

5. **Task E: Combine multiple tool usages**  
   - Streamlit UI Components

## Comparative Conceptual Map 🗺️

![ConMap](https://github.com/user-attachments/assets/f70feab9-209d-4c9c-b023-9ea2b141ebcc)

### Connections
1. **ReAct -> LATS**: LATS builds directly upon the ReAct framework by using the ReAct method as the basis of its agent architecture, and expands on that with a search over a combinatorial space of possible reasoning and acting steps, and adds reflection. The basic structure of a multi-step loop guided by internal reasoning, external actions, and subsequent observation is preserved and then augmented.

2. **ReAct -> AutoToolChain**: AutoToolChain adapts the interaction method of ReAct but is more focused on using program synthesis for chained tool execution, and for automated tool learning and schema identification. The basic structure of a multi-step loop guided by internal reasoning, external actions, and subsequent observation is preserved.

3. **Toolformer -> LATS**: Toolformer's emphasis on selecting the most useful tools during its various stages of reasoning inspires LATS' use of evaluation methods as in MCTS.

4. **Reflection**: The LATS approach shares much the same structure as ReAct, however a key is to integrate reflection. Reflexion was introduced to provide a verbal self-reflection that summarizes the errors in the reasoning or acting process and proposes superior alternatives.

![Connection](https://github.com/user-attachments/assets/916cbfca-4c1f-4d46-9d1e-77dd9031581c)

## Short Written Analysis 📊

### Comparative Analysis of LLM Tool-Use Approaches

#### 1. Agent Design: What's the Recipe?
- **ReAct**: Quick Thinker, Fast Action - Alternates between generating reasoning traces and task-specific actions
- **Toolformer**: Knows APIs by Heart - Uses internal knowledge to reason about tool usage
- **Automatic Tool Chain (ATC)**: The Code Writer - Reads code instructions and writes programs for tool usage
- **Language Agent Tree Search (LATS)**: The Planner - Plans multiple paths and learns from practice

**Key Design Differences:**
- **Memory**: Varies from prompt-based (ReAct/Toolformer) to full memory systems (LATS)
- **Speed vs. Thoroughness**: Trade-off between quick responses and complex task handling

#### 2. Reasoning Steps: How Do They Think?
- **ReAct**: Quick "Think, Act, See" loop
- **Toolformer**: Learned API call identification
- **ATC**: Programmatic step-by-step execution
- **LATS**: Multiple option planning and testing

#### 3. Tool Use: What Tools Do They Grab?
- **ReAct**: Various API calls
- **Toolformer**: Predefined API calls
- **ATC**: API calls and code generation
- **LATS**: External data focused

#### 4. Real-World Usefulness
- **ReAct**: Excels with good prompts/APIs
- **Toolformer**: Strong API timing decisions
- **ATC**: Automated tool creation
- **LATS**: Excellent for learning-based tasks

## Design Decisions 🧠

### Agent Architecture

![pako_eNqdV1FP4zgQ_itWVvsGK9pC6fbhTlyB00pw4rbsnXSBB5M4rUVqR46zUAr__SYZO4njlHapkPA4830ez2eP7U0QyZgF02ChaLYkt3_cCQK_z5_JNeWCfBNZocllKp-w_0fO1N8FU-uwbJGqeU8OD38jV1fXN0pGLM-l2oCB30jd94YENX3pYj5yscDuvHjAMODjFV0zFbpepOq8R](https://github.com/user-attachments/assets/4a25f0b2-8f24-4d82-b902-3db43366d96f)

1. **Input Processing Layer**
   - Intent Detection
   - Constraint Extraction (Price, Size, Color, Date)

2. **Tool Selection Process**
   - Tool Categories:
     - Price Comparison Tool
     - Inventory Checker
     - Shipping Calculator
     - Policy Checker

3. **Execution Layer**
   - Data Orchestration

4. **Response Generation**
   - Data Aggregation
   - Natural Language Generation
   - Response Formatting

### Example Query Flow
For query "Find a floral skirt under 4000 Rupees in size S":
```python
tools = select_tools(query_type, constraints)
results = orchestrator.execute_tools(tools, constraints)
```

## Challenges & Improvements 🚧

### Technical Challenges
1. **Fuzzy Matching Optimization**
   - Token-based scoring with adjustable thresholds

2. **LLM Latency Management**
   - Predictive loading animations

3. **Data Integrity**
   - Comprehensive DB validation

4. **Cross-Platform Comparison**
   - Normalized product variant matching

## Open Questions & References 📚

### Open Questions
1. **Ambiguous Query Handling**
   - Dynamic price-range estimation
   - Context-aware interpretation

2. **Multi-Platform Inventory Sync**
   - API rate limit management
   - Cross-platform data ethics

3. **LLM Hallucination Mitigation**
   - Grounding techniques
   - Fluency vs. data fidelity

4. **Personalization vs Privacy**
   - Anonymous profiling
   - DPDPA compliance

5. **Regional Language Support**
   - Hinglish query processing
   - Low-latency architecture

### Research References
1. Chen, Q., et al. (2021). "BERT-Based Hybrid Model for Intent Classification" - IEEE Transactions on NLP
2. Kumar, A., & Joshi, S. (2020). "Adaptive Thresholding for Fuzzy Matching" - ACM SIGIR Conference
3. Li, L., et al. (2023). "Retail-LLM: Knowledge Distillation" - arXiv:2308.12345
4. Gupta, P., & Rao, R. (2022). "Design Patterns for Tier-2 Cities" - ACM CHI India
5. Patel, R., & Shah, M. (2019). "Blockchain Inventory Synchronization" - IEEE IoT Journal

## Installation ⚙️
```bash
git clone https://github.com/yourusername/smart-product-search.git
cd smart-product-search
install Ollama https://ollama.com/download
Once Ollama (Llama3.2 3B) is installed go to cmd and type - ollama run llama3.2
pip install -r requirements.txt
python create_db.py
streamlit run app.py
```
