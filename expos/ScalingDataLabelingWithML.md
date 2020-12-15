## Scaling Data Labeling with Machine Learning at Scale 

| Date | Title | Speaker | Type |   
| ---- | ----- | ------- | ---- |
| 07/12/2020 | Scaling Data Labeling with ML  | Felix Lau | Expo-Workshop |

### Context: The Scale AI Platform
- API for training data; customer sends the data they want labeled and what instances need to get labeled
- Scale does Automated Labeling, Removes bad samples and lets global taskers finetune labeling


### ML Model Use Cases
- 1) Prelabeling new images with pretrained models; 2) Active Tooling (labelers can work with intermediate outputs of the model) f.e. SuperPixel will group pixels together and as such manual task force will not have to select each pixel); 3) Quality Assurance (Linting), detect with a likelihood object detector that everything has been labeled and boxes are tight enough


### Heterogeneous Datasets

**Challenge 1: Diversity in Data Domain**
- diverse background, objects, weather, day of time, etc.
- objects to be annotated varies per dataset as well
- labeling rules differ across datasets (f.e. some want the side mirror to be included or not for car labeling)
- training across datasets increases accuracy and removes ramp up time

    Approach 1: Train one model per object to be detected  
    Approach 2: Super Taxonomy
    f.e. Construction Worker, pedestrian etc. are in different dataset and share workers -> One Person Class to pretrain on

### Continual Learning
- Datasets follow a long distribution, as such we want to balance between learning the tail without catastrophic forgetting
- The tail is more interesting, because those are hard edge cases
- Need to be able to adapt to a new distribution while avoiding catastrophic forgetting
    -> Naive approach: Train different models from scratch for different datasets
- Better approaches: 
  Approach 1: Coreset method: Learning to select a subset of images that yields similar accuracy as trained on a full dataset -> Choose samples closest to cluster center // Removing unforgettable samples: increase accuracy doing training
  Approach 2: Easy samples reduce loss very fast, Hard samples loss stays somewhat high, Edge cases loss goes up during training -> Tail end of the distribution -> Oversample these edge cases so finetuned model does not forget
  **Approach 3: Dataset Distillation: Make synthetic images that distill knowledge of a full dataset** -> This condensed data can be used to not get catastrophic forgetting  
