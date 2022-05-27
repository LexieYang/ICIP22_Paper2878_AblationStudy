# ICIP22_Paper2878_AblationStudy
This repository contains more experimental results

# 1. Effectiveness of Multi-scale Feature Aggregation Structure
In the Multi-scale Channel-Spatial Attention Module (M-CSAM) (shown in *Figure 1*), we adopt a multi-scale feature aggregation structure to explore features from four different receptive scales. Features obtained with larger receptive fields tend to be more robust to texture and color variation, while features from smaller receptive fields focus more on details. The combination of features from different receptive fields is shown to be effective for masked region recovery as shown in *Figure 2* and *Table 1*.

To illustrate the effectiveness of multi-scale structure, we performed an experiment without the multi-scale structure. As shown in *Table 1*, when the multi-scale structure is removed, the performance drops in terms of all metrics, namely SSIM, PSNR and $l_1$ loss. *Figure 2* provides some examples for qualitative comparison. As can be seen, without multi-scale feature aggregation module, the recovered regions have distorted areas (see *Figure 2(c)* and *Figure 2(d)*). The network equipped with multi-scale feature aggregation module incorporates larger receptive fields and a better semantic understanding. Therefore, with the assistance of the multi-scale feature aggregation module, the recovered content is more consistent with the ground truth, and has better continuity and texture.

| ![cvpr_minmin2022_figure123-Copy of Page-1 drawio](https://user-images.githubusercontent.com/63827451/170769286-01d65104-f24b-489a-8b15-1c7d4efc22b3.png) |
|:--:|
| *Figure 1. The structure of M-CSAM* |



| | SSIM<sup>+</sup> | PSNR<sup>+</sup> | l1 loss<sup>-</sup> | 
| ---------------- | ---------------- | ---------------- | ---------------- |
| M-CSAM | **0.9511** | **30.3885** | **0.0076** |
| CSAM | 0.9454 | 29.6126 | 0.0084 |

*Table 1. The effect of multi-scale feature aggregation structure. <sup>+</sup>Higher is better. <sup>-</sup>Lower is better*.


| ![Screen Shot 2022-05-27 at 3 22 47 PM](https://user-images.githubusercontent.com/63827451/170777078-a82a38c0-93a7-4c78-b170-0da483947433.png) |
|:--:|
| *Figure 2. **Qualitative comparison of models with and without multi-scale feature aggregation structure.** First row: input images with face masks; Second row: ground-truth images; Third row: results from the network with multi-scale feature aggregation structure; Fourth row: results from the network without multi-scale feature aggregation structure (best viewed when zoomed-in).* |



## 2. Effectiveness of local area supervision 
Instead of supervising the generation of whole images, our network focuses only on recovering the masked region, which has lower pixel variance compared to the whole image. We conduct further experiments to verify our conjecture that local error supervision is better than full image supervision. We train the model in two ways: (i) one focusing on the direct output from the inpainting network, $I_r$ and (ii) one focusing on the synthetic output, $I_{syn}$. The results are provided in *Table 2*, showing that supervision only over the masked region is beneficial for learning in terms of SSIM PSNR and $l_1$ loss. 

| | SSIM<sup>+</sup> | PSNR<sup>+</sup> | l1 loss<sup>-</sup> | 
| ---------------- | ---------------- | ---------------- | ---------------- |
| local supervision | **0.9511** | **30.3885** | **0.0076** |
| full supervision | 0.9441 | 29.6932 | 0.0088 |

*Table 2. The comparison of supervision over masked region and the whole image.  <sup>+</sup>Higher is better. <sup>-</sup>Lower is better*.


| ![Screen Shot 2022-05-27 at 4 14 32 PM](https://user-images.githubusercontent.com/63827451/170783409-a7b2e2aa-9f53-4fdb-8206-8b800d32c3af.png) |
|:--:|
| *Figure 3. **Qualitative comparison of local area supervision and the supervision over the whole image.** First and second rows are the input masked image and ground-truth images, respectively. The third and fourth rows show the results from local supervision and from full supervision, respectively.* |


The qualitative comparison between two ways of supervision is provided in *Figure 3*. The results from the local supervision have less color diffusion and structure distortion. However, for the results from full supervision, the recovered pixels have larger color discrepancy with the surrounding unmasked pixels when comparing the third and forth rows in *Figure 3(a)*, *Figure 3(b)*, *Figure 3(d)* and *Figure 3(f)*. In addition, when the third and forth rows of *Figure 3(a)* and *Figure 3(d)* are compared, it can be seen that the local supervision strategy can help the network generate more plausible and clear texture, such as the texture of nose and mouth.


