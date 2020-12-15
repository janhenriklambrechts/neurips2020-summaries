## Practical Limitations of Today's Deep Learning in Healthcare

| Date | Title | Speaker | Type |   
| ---- | ----- | ------- | ---- |
| 12/12/2020 | Practical Limitations for Deep Learning in Healthcare | Andrew Ng | Workshop (ML4Health) |

### Introduction 
- Big gap between research and production setting where we can actually help patients
- F.e. a paper from Andrew NG "DL can achieve radiologist performance on 11 pathologies and did not achieve radiologist-level performance on 3 pathologies
    -> ML sometimes does as well as  Stanford level Radiologists
- This does not stay exclusive to this kind of healthcare, we have had succesful (un)supervised ML research in the areas of Brain Aneurysms, Appendicitis, Liver cancer etc. - in about half of them we match or surpass human-level performance (diagnostic accuracy)
- If there are so many papers by so many groups showing that there are learning algorithms that do better than doctors - Why arent these systems widely deployed in hospitals yet?
- ML has a **PoC to Production Gap problem**: Bridge between Jupyter Notebook / research paper and a system in production is really, really large. 

### ML model vs. ML system
- Google Paper: ML is high-interest stratichot of technical debt
- This is the gap between a ML Model (something that has learned a mapping) and a ML System (ML Model in production that actually helps patients) 

### Pratical Challenges of ML Systems
- Small Data issues
- Robustness & Generalization 
- Safety & Regulation

### Small data
- Machine Learning works well when dataset looks uniform (as opposed to long-tailed/ skewed data)
- F.e. lets zoom in to the claim: "Radiologist-level performance on 11 pathologies and not on 3" 
    - In pathologies where there were about 11000 examples, ML algo did as well as the Radiologist
    - However, in pathologies where there are 110 examples, ML does significantly worse
    - **A ML Model can do very badly on rare classes and achieve very good average performance** -> This is not OK for deployment

### Humans vs ML
- Easy for ML: Diagnose pneumonia given 10.000 labeled images
- Hard for ML: Diagnose a rare condition from 10 images of a medical textbook explaining that condition

### Time to rethink human-level performance (HLP)
- Academia often aspires to beat human-level performance on benchmarks -> It can play a large role in establishing a baseline or to perform error analysis
- But for practical systems: if HLP is low (two doctors agree only 60% of the time), consider instead if there is a way to label more consistently 
    -> Instead of saying "Lets beat this easy HLP!", help solving the HLP first 
    -> This also gives you better data! Making your ML better. If you have little amounts of data, then data labeling accuracy is absolutely critical! 

### Small Data Solutions
- **Data Augmentation**: Set up creative automated pipelines for data augmentation
- **Data Synthesis**
- **GANs**
- **Pretraining**

### Robustness & Generalization
- True for many industries, but also in healthcare
- Slightly different system in different hospital can lead to large performance drop

### Safety & Regulations
- The standards we need to expect an ML system to hold have not been established yet
- Patient safety is paramount, How do we make sure an ML algorithm does not cause harm
- Clear processes to audit an ML system to see if it is meeting that standard
    
### Palliative (end of life) care
- Doctors make few palliative care referral -> because this feels like "giving up on a patient"
- Volume of patients is just too much
- Probability of people dieing to see which could be considered fo r palliative care
- One of the things we learned: "Who are you to decide my patient will die" -> Spend enough time on change management
- Once the doctors saw the explanation/visualization to see that the results are plausible

### Full cycle of an ML Project
1. **Scoping:** Decide on a problem to solve
    -> Requires cross-functional brain-storming
2. **Data:** Acquire data to model
3. **Modeling:** Build/Train AI Models
    -> In AI research, we often keep training data fixed and tune hyperparams in algos. However, often IRL it is useful to keep algo fixed and change the training data and hyperparams
4. **Deployment:** Run in production to create value
-> Deploy fast and iterate and improve

### ML as a systematic engineering discipline
- Some directions for full-cycle of ML:
    - Data editing and data versioning tools
    - Performance Auditing
    - Safety Monitoring and Regulatory Compliance
    - MLOps Tools for healthcare
