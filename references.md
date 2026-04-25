# References

All citations in the notebook and in the final annotated document are numbered according to the list below.

**Citation style:** numbered square brackets, for example `[1]` for a whole paper and `[1, Sec. 3]` or `[1, Fig. 5]` to point to a specific section, figure, or table inside a paper.

---

## Primary paper (the one we are annotating)

[1] He, K., Chen, X., Xie, S., Li, Y., Dollar, P., and Girshick, R. (2022). Masked Autoencoders Are Scalable Vision Learners. In *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*, pp. 16000 to 16009.

Paper PDF: https://openaccess.thecvf.com/content/CVPR2022/html/He_Masked_Autoencoders_Are_Scalable_Vision_Learners_CVPR_2022_paper.html

BibTeX:
```
@inproceedings{he2022masked,
  title     = {Masked Autoencoders Are Scalable Vision Learners},
  author    = {He, Kaiming and Chen, Xinlei and Xie, Saining and Li, Yanghao and Doll{\\'a}r, Piotr and Girshick, Ross},
  booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  pages     = {16000--16009},
  year      = {2022}
}
```

---

## Foundational references cited inside our annotation

[2] Dosovitskiy, A., Beyer, L., Kolesnikov, A., Weissenborn, D., Zhai, X., Unterthiner, T., Dehghani, M., Minderer, M., Heigold, G., Gelly, S., Uszkoreit, J., and Houlsby, N. (2021). An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale. In *International Conference on Learning Representations (ICLR)*.

*Role in our annotation:* the Vision Transformer (ViT) backbone that MAE's encoder is built on. Referenced whenever we talk about patch embedding, positional embeddings, or the ViT-B / ViT-L / ViT-H sizes.

[3] Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, L., and Polosukhin, I. (2017). Attention Is All You Need. In *Advances in Neural Information Processing Systems (NeurIPS)*.

*Role in our annotation:* source of the Transformer block used inside both the encoder and the decoder. Multi-head attention, the LayerNorm placement, and the feed-forward MLP pattern all come from this paper.

[4] Devlin, J., Chang, M.-W., Lee, K., and Toutanova, K. (2019). BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding. In *Proceedings of NAACL-HLT 2019*.

*Role in our annotation:* source of the masked-prediction pre-training objective that MAE adapts to images. Referenced for the 15% vs 75% masking ratio contrast, the learned mask token, and the general philosophy of "remove a portion of the data and learn to predict it."

[5] Krizhevsky, A. (2009). Learning Multiple Layers of Features from Tiny Images. Technical Report, University of Toronto.

*Role in our annotation:* the CIFAR-10 dataset used for the MWE. Accessed through `torchvision.datasets.CIFAR10`.

[6] Paszke, A., Gross, S., Massa, F., Lerer, A., Bradbury, J., Chanan, G., Killeen, T., Lin, Z., Gimelshein, N., Antiga, L., Desmaison, A., Kopf, A., Yang, E., DeVito, Z., Raison, M., Tejani, A., Chilamkurthy, S., Steiner, B., Fang, L., Bai, J., and Chintala, S. (2019). PyTorch: An Imperative Style, High-Performance Deep Learning Library. In *Advances in Neural Information Processing Systems (NeurIPS)*.

*Role in our annotation:* the framework used for all model code in the notebook.

[7] Loshchilov, I., and Hutter, F. (2019). Decoupled Weight Decay Regularization. In *International Conference on Learning Representations (ICLR)*.

*Role in our annotation:* AdamW, the optimizer used by the original paper. Our MWE uses plain Adam for simplicity; Person 2's Training Loop section discusses AdamW and the cosine schedule in detail.

[8] Vincent, P., Larochelle, H., Bengio, Y., and Manzagol, P.-A. (2008). Extracting and composing robust features with denoising autoencoders. In *Proceedings of the 25th International Conference on Machine Learning (ICML)*.

*Role in our annotation:* the classical denoising autoencoder framework. The MAE paper places itself explicitly in this lineage, so we cite it when discussing how MAE generalizes denoising autoencoders (see [1, Sec. 2, "Autoencoding"]).

[10] Tong, Z., et al. (2022). VideoMAE: Masked Autoencoders are Data-Efficient Learners for Self-Supervised Video Pre-Training. NeurIPS.
*Role: future work on video

[11] Huang, P. D., et al. (2022). Masked Autoencoders that Listen. NeurIPS.
*Role: future work on audio

[12] Pang, Y., et al. (2022). Masked Autoencoders for Point Cloud Self-supervised Learning. Proceedings of the European Conference on Computer Vision (ECCV).
*Role: future work on 3d point clouds

[13] Guo, Z., Li, X., & Heng, P. A. (2023). Joint-MAE: 2D-3D Joint Masked Autoencoders for 3D Point Cloud Pre-training. Proceedings of the International Joint Conference on Artificial Intelligence (IJCAI).
*Role: future work on 3d point clouds


---

## Code reference

[9] Facebook AI Research (FAIR). Official MAE implementation.

Repository: https://github.com/facebookresearch/mae

*Role in our annotation:* consulted for the shuffle / unshuffle masking convention and the asymmetric encoder-decoder layout. All code in our notebook was written from scratch for readability; any resemblance in variable names (for example `ids_restore`, `ids_keep`) follows the convention used in the official repo.

---

## Course material

[10] Course project description, CS 577 Deep Learning, Spring 2026.

*Role in our annotation:* source of the project requirements, including the MWE specification and the grading criterion that emphasizes "maximizing understanding" over benchmark performance.

---

## How to use these references across the three sections

| Section | Most-cited references |
|---|---|
| Background (Person 2) | [1], [2], [4], [8] |
| Model architecture (my section) | [1], [2], [3] |
| Training loop (Person 2) | [1], [7] |
| MWE / ablation (my section) | [1], [5], [6] |
| Discussion and future directions (Person 3) | [1] and whichever follow-up papers Person 3 chooses to compare against |

When the final PDF is assembled, this list becomes the last section. Every `[N]` citation in any of the three sections must resolve to an entry here, and nothing extra should appear that is not actually cited somewhere. Easy sanity check at assembly time: search the document for every `[N]` and make sure N appears in this list.
