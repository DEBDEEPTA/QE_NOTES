### 1.  SOFTWARE TESTING
* _Software testing ensures that an application works as expected, meets user requirements, and fails safely when something goes wrong._
#### 1.1 TESTING DIMENSIONS
  1. _Type of Testing (What we test)_ 
  2. _Levels of Testing (When/Where we test)_
  3. _Test Classification (Why we test)_
___

### 2. TYPE OF TESTINGS
* _Functional Testing_
* _Non-Functional Testing_

![testing_types.jpg](imgs/testing_types.jpg)
![testing_ov_gg.png](imgs/testing_ov_gg.png)
___
### 3. LEVELS OF TESTING
![Level_of_testings.jpg](imgs/Level_of_testings.jpg)
### 4. TEST CLASSIFICATION
![test_classification.jpg](imgs/test_classification.jpg)
![ret_vs_regt.png](imgs/ret_vs_regt.png)
#### 4.1 Types of Regression Testing
![reg_t_types.png](imgs/reg_t_types.png)
#### 4.2 SMOKE VS SANITY TESTING

| Aspect  | Smoke           | Sanity           |
| ------- | --------------- | ---------------- |
| Scope   | Broad           | Narrow           |
| When    | New build       | After minor fix  |
| Purpose | Build stability | Fix verification |
| Depth   | Shallow         | Deep             |
![somke_vs_sanity.png](imgs/somke_vs_sanity.png)
![smoke_sanity_flow.png](imgs/smoke_sanity_flow.png)

### 5. MANUAL TESTING TYPES
| Criteria             | White Box                                 | Black Box               | Gray Box                         |
| -------------------- |-------------------------------------------| ----------------------- | -------------------------------- |
| Code Knowledge       | Full                                      | None                    | Partial                          |
| Who Performs         | Developers                                | Testers                 | Testers (technical)              |
| Focus                | Internal logic                            | External behavior       | Both                             |
| Programming Required | Yes                                       | No                      | Some                             |
| Testing Level        | Unit Testing                              | System/Acceptance       | Integration/System               |
| Techniques           | Path coverage, Branch coverage, loop Test | BVA, EP, Decision table | API testing, DB validation       |
| Main Goal            | Code correctness                          | Functional correctness  | Functional + Internal validation |
#### 5.1 ANALOGY
* Black Box → Drive the car and see if it works
* White Box → Open engine and check internal components
* Gray Box → Drive car + check engine diagnostics

### 6. ADHOC/MONKEY/GORRILA TEST
![adhoc_t1.png](imgs/adhoc_t1.png)
![adhoc_t2.png](imgs/adhoc_t2.png)