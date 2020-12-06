## Computer Vision at Netflix

| Date | Title | Speaker | Type |   
| ---- | ----- | ------- | ---- |
| 06/12/2012 | Recent Trends in Personalization at Netflix | Cristina Segalin, Dong Liu | Expo-Workshop |

### Introduction
- Automating Creative Artworks from Netflix Series for personalization 
- Fully end-to-end: Full-length video -> CV Model -> Output artwork candidates
- Character Recognition / Object Detection / Scene Understanding etc. + Crop Logo placement etc. 

### Large Scale video dataset opportunities and challenges
- Video Understanding
- Video summarization
- Content Retrieval
- Content Recommendation
- VFX
- Fairness in recommendation

### Case study: Character-focused Video Thumbnail Retrieval
- **Goal**: Retrieve character-focused video thumbnail candidates given full-lenght shows
- **Problem Statement**: Score each frame of a video in terms of thumbnail candidate suitability
- **Application**: Narrow down search space for creators to choose from

**Thumbnail criteria**
- Show a primary (prominent) character
- Have a suitable face expression (no blinking etc.)
- Learn the face expressions directly from a thumbnail dataset

**Character Interaction Graph**
- Goal: Model character prominence and their interactions
- How: Detect faces, extract face feature embeddings and cluster those -> Each cluster (should) represent a character and larger clusters will correspond to primary characters; If two faces appear in the same frame that is an interaction 
- **Node** is a character or face-cluster; **Edge** is the co-occurence of two characters

**Facial Expression**
- Filter out faces where character is blinking, speaking, has motion blur
- VGG-face backbone with binary classification on expressions
- For every frame we get a frame-level score with this expression model

**Evaluation**
- 20 videos annotated frames for a good candidate by humans

### Case study: Computer Vision Assisted Video Creation
- **Goal**: Given a full length video choose the best video clip for promotion
- **Applications**: Create trailers and supplemental videos

**Movie Trailer-Worthy Moment Detection**
- Can we develop a computer vision model to automatically detect trailer moments in full-length movies 
- [Paper](https://arxiv.org/abs/2008.08502) (ECCV 2020)
- To get shot boundaries are actually very easy, just get the pixel difference between two frames
- Weakly-Supervised Trailerness Ranking -> We have a dataset of full movies with trailers (so positive labels) but no negative labels
- For each shot in the movie, they get an attention weight in respect to all shots. We take this matching scores and treat them as soft labels. Trailer moments we score higher.
- 3D ResNet-34 with a Contrastive attention to match shots in movie with match in the trailer

**Evaluation**
- Accuracy withing top 10 detected moments 85% on test data meaning that IRL 8.5 of the detected moments were actually used as  trailers. 
- Also qualitatively good, lowest scored are often title shots etc.
