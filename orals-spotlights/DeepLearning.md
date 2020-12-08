## Multiscale Deep Equilibium Models
- Shaojie Bai et al.

### Explicit vs Implicit Layers
- Explicit Layers explicitly perform operations in a hierarchy of hidden scales
    -> We built a dynamic graph to calculate gradient in backprop
- Implicit models try to find a dynamic equilibium solution, we dont need to store any intermediate state -> so good for not having to store intermediate states in memory
- This paper works on applying these models for large scale CV tasks, giving on-par results
- Root solving for equilibrium points
- But if we have only one shallow layer, how can we get deep feature representations? 
    -> Do it at multiple scales at the same time -> Use multiple resolutions for different tasks: small resolution for classification, large images for segmentation -> No feature pyramids 
- Batch Norm & Dropout is not very useful at MDEQ because they make the Jacobian harder to approximate
- Works very, very well - comparable to ResNet-50 on ImageNet
- Slower but O(1) memory


