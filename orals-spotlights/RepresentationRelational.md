## Representation / Relational

### Learning Physical Graph Representations of Visual Scenes
- Daniel Bear et al.
- CNNs can make non-sensical predictions like objects dissolving, because they do not really *understand* **physical structure** of these objects
- The first step towards understanding, is having a representation: tis paper: a graph that represents a scene in which
    - Objects are nodes
    - Edges are relationships
    - Each node has a vector that encodes physical attributes
- Now: Lets learn a model that can produce these graphs from images: 
    - ConvRNN: for mixing lower-level and higher-level features
               -> We can think of this as an hour-glass network but with more flexibility on how to combine these features
    - **Learnable Graph Pooling**: transform set of nodes into one big node -> This corresponds to multiple parts in object belonging together (f.e. background)
    - Use these learned graph regions + segmentation maps to predicts latent codes that encode physical properties
    -> As such that network has latent vectors that correspond to spatial (x,y,z) and color attributes and many others
- PSGNets substantially improve existing unsupervised object discovery methods + much more efficient
- However, we can learn much more from motion than texture about objects physicality -> We can use PSGNets to learn motions -> When ussing movement as well it works even better

### Multi-label Contrastive Predictive Coding
- Jiaming Song
- **Self-supervised Representation Learning**: Learning to map observations to *compact* yet *informative* representations without labels
- One key idea for this task: Contrastive Predictive Coding (ML-CPC) -> Multi-class classification to find 1 **positive pair** among M pairs (M example images, choose one that corresponds)
- Issue with CPC: with more (N > M) negative pairs we need more compute and data. Yet with more negative samples we have better performance
- **Can we get more negative samples without compute?**
    - Multi-Label Contrastive Predictive Coding (ML-CPC) -> Increases the amount of effective negative samples in CPC
    - Simple implementation, theoretical guarantees and no compute
    - CPC: 2 problems, each problem has one label and M=4 examples
    - ML-CPC: 1 problem with two labels and M=8 examples -> Harder because now you can choose two images from the same group  -> Soft labels that sum to 1 (0.5 and 0.5)
- M samples per reference samples: Can we increase upper bound without more negative samples?  -> Corresponding alpha 
- Application - KD: Beats SOTA easily

### Equivariant Maps for Hierarchical Structures
- Renhao Wang
- Hierararchy of structures are not really studied for equivariant networks

