## Self-Driving at Cruise

| Date | Title | Speaker | Type |   
| ---- | ----- | ------- | ---- |
| 06/12/2020 | Driving New Frontiers of ML with Cruise | Zhaoyin Jia, Tianshi Gao, Cristina Schiau  | Expo-Workshop |

### Cruise Data Pipeline
- Cameras, LIDARs, Radars, GPS, etc. all get uploaded to the cloud: about 1000 miles a day -> Goes through labeling pipeline (bounding boxes, segmentation etc.) 
- Zhaoyin leads Perception as a Principal Research Scientist at Cruise
- One of the biggest challenges is that long tail situations is captured in dataset  -> the edge cases, a data problem

### Motion Planning
- Get a desired future state, maxime safety and comfort on the way there
- Computer Vision difference between industry and academia: all these signals with different latencies need to be fused
- Thousands of partially occluded objects
- Bounding boxes, semantic understanding, scene understanding, make low confidence predictions when needed
- How to get confidence that you have every situation under control : use a LiDAR etc. to maybe not be able to recognize them but be able to predict where they are going and predict their future motion  -> Also in simulation we can sweep for all possible parameters and create more data this way
- Self-supervised: Future reveals itself // Also fully supervised: Film a certain crossroad and get an empirical distribution for that, train models to be able to model these distributions
