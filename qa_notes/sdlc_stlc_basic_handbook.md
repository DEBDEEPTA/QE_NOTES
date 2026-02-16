## 1. RELATIONSHIP B/W SDLC & STLC
```markdown
    SDLC Phase                Corresponding STLC Activity
    -------------------------------------------------------
    Requirement               Requirement Analysis
    Design                    Test Planning + Test Design
    Coding                    Test Case Preparation
    Testing                   Test Execution
    Deployment                UAT / Production Validation
    Maintenance               Regression Testing

```
```markdown
    Note ->         STLC runs inside the SDLC testing phase but starts early.
    
    Difference ->   SDLC builds the product.     
                    STLC validates the product.
```
___
## 2. COMPARISON TABLE
| Parameter         | SDLC                            | STLC                        |
| ----------------- | ------------------------------- | --------------------------- |
| Full Form         | Software Development Life Cycle | Software Testing Life Cycle |
| Purpose           | Develop software                | Validate software           |
| Scope             | Entire software development     | Only testing activities     |
| Focus             | Building product                | Ensuring quality            |
| Owned By          | Developers + Architects + PM    | QA / Test Engineers         |
| Starts From       | Requirement gathering           | Requirement analysis        |
| Ends At           | Maintenance                     | Test closure                |
| Includes Coding?  | ✅ Yes                           | ❌ No                        |
| Includes Testing? | ✅ Yes                           | ✅ Only testing              |
| Main Deliverable  | Working software                | Test reports & defect logs  |
| Documents Created | SRS, HLD, LLD                   | Test Plan, Test Cases, RTM  |
| Entry Criteria    | Business idea                   | SRS document                |
| Exit Criteria     | Product deployed                | Test closure report         |
| Defect Handling   | Developers fix defects          | QA logs defects             |
| Dependency        | Independent lifecycle           | Dependent on SDLC           |
| Objective         | Build system                    | Break system (find bugs)    |
| Success Metric    | Product delivered               | Zero critical defects       |
---
## 3. PHASE MAPPING
| SDLC Phase  | STLC Phase           | Output             |
| ----------- | -------------------- | ------------------ |
| Requirement | Requirement Analysis | RTM                |
| Design      | Test Planning        | Test Plan          |
| Coding      | Test Case Design     | Test Cases         |
| Testing     | Test Execution       | Defect Report      |
| Deployment  | Validation           | UAT Report         |
| Maintenance | Regression           | Updated Test Suite |
___
## SOFTWARE DEVELOPMENT MODELS
    
| Model     | How It Implements SDLC                            |
| --------- | ------------------------------------------------- |
| Waterfall | Executes phases sequentially                      |
| V-Model   | Links each development phase with testing phase   |
| Agile     | Executes all phases in short iterations (sprints) |
| Spiral    | Repeats SDLC phases with risk analysis            |
| DevOps    | Integrates SDLC with continuous delivery          |

### Key Points
* 🔒 Fixed & stable → Waterfall
* 🏥 Safety-critical → V-Model
* 🔄 Frequently changing → Agile
* ⚠ High risk & complex → Spiral
* 🚀 Continuous deployment → DevOps
### Comparison Table
| Criteria                         | **Waterfall Model**                        | **V-Model**                                    | **Spiral Model**                     |
| -------------------------------- | ------------------------------------------ | ---------------------------------------------- | ------------------------------------ |
| **Type**                         | Linear Sequential Model                    | Verification & Validation Model                | Risk-Driven Iterative Model          |
| **Approach**                     | Step-by-step execution                     | Development & Testing in parallel mapping      | Iterative cycles with risk analysis  |
| **Flow Structure**               | Requirement → Design → Dev → Test → Deploy | Left side (Dev) mapped to Right side (Testing) | Repeated loops (spirals)             |
| **Flexibility**                  | ❌ Very Low                                 | ❌ Low                                          | ✅ High                               |
| **Requirement Stability Needed** | Must be very clear & fixed                 | Must be clear & well-defined                   | Can handle changing requirements     |
| **Risk Management**              | ❌ Not handled explicitly                   | ❌ Limited                                      | ✅ Strong risk analysis in each cycle |
| **Testing Involvement**          | Testing after development                  | Testing planned from beginning                 | Testing in every iteration           |
| **Customer Involvement**         | Minimal after requirement phase            | Moderate                                       | High (at end of each spiral)         |
| **Cost of Change**               | Very High                                  | High                                           | Moderate (changes allowed per cycle) |
| **Complexity Handling**          | Good for simple projects                   | Suitable for medium complexity                 | Best for large & complex projects    |
| **Documentation**                | Heavy documentation                        | Heavy documentation                            | Moderate documentation               |
| **Project Size Suitability**     | Small to Medium                            | Medium                                         | Large & Critical systems             |
| **Time to Market**               | Slow                                       | Slow                                           | Moderate                             |
| **Control & Predictability**     | High predictability                        | High control                                   | Medium predictability                |


___
