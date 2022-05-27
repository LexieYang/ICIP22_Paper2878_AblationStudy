# ICIP22_Paper2878_AblationStudy
This repository contains more experimental results

# Effectiveness of Multi-scale Feature Aggregation Structure
In the Multi-scale Channel-Spatial Attention Module (M-CSAM) (shown in Figure 1), we adopt a multi-scale feature aggregation structure to explore features from four different receptive scales. Features obtained with larger receptive fields tend to be more robust to texture and color variation, while features from smaller receptive fields focus more on details. The combination of features from different receptive fields is shown to be effective for masked region recovery as shown in Figure 2 and Table 1.

To illustrate the effectiveness of multi-scale structure, we performed an experiment without the multi-scale structure. As shown in Table 1, when the multi-scale structure is removed, the performance drops in terms of all metrics, namely SSIM, PSNR and l1 loss. Figure 2 provides some examples for qualitative comparison. As can be seen, without multi-scale feature aggregation module, the recovered regions have distorted areas (see Figure 2(c) and Figure 2(d)). The network equipped with multi-scale feature aggregation module incorporates larger receptive fields and a better semantic understanding. Therefore, with the assistance of the multi-scale feature aggregation module, the recovered content is more consistent with the ground truth, and has better continuity and texture.

| ![cvpr_minmin2022_figure123-Copy of Page-1 drawio](https://user-images.githubusercontent.com/63827451/170769286-01d65104-f24b-489a-8b15-1c7d4efc22b3.png) |
|:--:|
| *Figure 1. The structure of M-CSAM* |



| | SSIM<sup>+</sup> | PSNR<sup>+</sup> | l1 loss<sup>-</sup> | 
| ---------------- | ---------------- | ---------------- | ---------------- |
| M-CSAM | **0.9511** | **30.3885** | **0.0076** |
| CSAM | 0.9454 | 29.6126 | 0.0084 |

Table 1. The effect of multi-scale feature aggregation structure. +Higher is better. -Lower is better 


| ![Screen Shot 2022-05-27 at 3 22 47 PM](https://user-images.githubusercontent.com/63827451/170777078-a82a38c0-93a7-4c78-b170-0da483947433.png) |
|:--:|
| *Figure 2. **Qualitative comparison of models with and without multi-scale feature aggregation structure.** First row: input images with face masks; Second row: ground-truth images; Third row: results from the network with multi-scale feature aggregation structure; Fourth row: results from the network without multi-scale feature aggregation structure (best viewed when zoomed-in).* |
