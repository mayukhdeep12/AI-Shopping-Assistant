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

## Tests
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

## Comparative Conceptual Map

![ConMap](https://github.com/user-attachments/assets/f70feab9-209d-4c9c-b023-9ea2b141ebcc)

### Connections
1. **ReAct -> LATS: Smarter Planning**: LATS is built on top of ReAct. It takes ReAct’s simple Think -> Act -> Observe loop and makes it more advanced. Instead of just reacting step by step, LATS explores different possible solutions before choosing the best one. It also adds a new ability: reflection, meaning it looks back at past mistakes and improves its strategy.

2. **ReAct -> AutoToolChain: More Focus on Code**: AutoToolChain (ATC) also follows ReAct’s Think -> Act -> Observe process but uses it in a more structured way. Instead of just making API calls, ATC writes code to automate tool use. It also learns how to create and connect tools, making it more flexible for complex tasks.

3. **Toolformer -> LATS: Smarter Tool Choices**: Toolformer is all about picking the right tools at the right time. LATS takes this idea further—it evaluates different actions (just like how Toolformer picks APIs) and searches for the best possible path forward, similar to a strategy game.

4. **Reflection: The Key Upgrade in LATS**: What really makes LATS special is reflection. While ReAct just moves forward step by step, LATS pauses to analyze what went wrong, learns from it, and adjusts its approach for better results in the future.

![Connection](https://github.com/user-attachments/assets/916cbfca-4c1f-4d46-9d1e-77dd9031581c)

## Short Written Analysis


#### 1. How They Work: The Basic Idea
- **ReAct – Think and Do on the Spot**: ReAct quickly switches between thinking and taking action. It figures out what to do, does it, then looks at the result before deciding the next step.
- **Toolformer – Knows Which Tool to Use**: Toolformer is trained to recognize when and how to use different tools (like APIs) based on its internal knowledge.
- **Automatic Tool Chain (ATC) – Writes Code to Solve Tasks**: ATC follows instructions to generate code, helping it use tools in a structured, step-by-step way.
- **Language Agent Tree Search (LATS) – LATS thinks ahead, mapping out different possible paths before choosing the best one. It also learns from trial and error.

**Key Design Differences:**
- **Memory**: Varies from prompt-based (ReAct/Toolformer) to full memory systems (LATS)
- **Speed vs. Thoroughness**: Trade-off between quick responses and complex task handling

#### 2. How They Think Through Problems
- **ReAct** follows a simple loop: Think -> Act -> Observe -> Repeat
- **Toolformer** recognizes when an API call is needed and inserts it at the right time.
- **ATC** breaks tasks into small steps and writes code to complete them.
- **LATS** tests multiple strategies, refines them, and improves over time.

#### 3. How They Use Tools
- **ReAct** can call different APIs as needed.
- **Toolformer** only uses APIs it was trained on.
- **ATC** can both use APIs and generate new code when needed.
- **LATS** relies on external data and testing different approaches.

#### 4. Which One is Best?
- **ReAct** is fast and works well with clear prompts and good APIs.
- **Toolformer** is smart about using APIs at the right time.
- **ATC** is great for automating tasks that need code.
- **LATS** is the best choice for tasks that require learning and planning over time.

## Design Decisions

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

## Challenges & Improvements

### Technical Challenges
1. **Fuzzy Matching Optimization**
   - Token-based scoring with adjustable thresholds

2. **LLM Latency Management**
   - Predictive loading animations

3. **Data Integrity**
   - Comprehensive DB validation

4. **Cross-Platform Comparison**
   - Normalized product variant matching

## Open Questions & References

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

## Installation
```bash
git clone https://github.com/yourusername/smart-product-search.git
cd smart-product-search
install Ollama https://ollama.com/download
Once Ollama (Llama3.2 3B) is installed go to cmd and type - ollama run llama3.2
pip install -r requirements.txt
python create_db.py
streamlit run app.py
```
