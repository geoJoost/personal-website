---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Few-shot learning with SAM"
summary: "Can scene-specific vision foundation models outperform existing fully-trained global models for marine debris segmentation?"
authors: [admin]
tags: [Wageningen UR, programming, geovisualization]
categories: []
date: 2024-08-02T20:30:57+02:00

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

This post covers the second half of my MSc thesis: where I worked on improving marine debris segmentation with deep learning methods. The first half was spent developing the SAMSelect algorithm, an algorithm designed to select the band or index combination that achieves the best RGB information for marine debris. It's work and results are currently being worked on for publication, but it serves as the foundation for few-shot learning with the Segment Anything Model in the second half of my thesis.

## The challenge of marine debris segmentation
Marine debris detection is an important aspect of environmental conservation, and effective segmentation in satellite imagery is key to the identification and monitoring of debris. Recently, deep learning has been showing great promise in image segmentation tasks (Kikaki et al., 2024; Rußwurm et al., 2023). However, applying these models to marine debris is particularly challenging due to the scarcity of labeled data. While large datasets are often used to train deep learning models, acquiring enough data on marine debris is not only expensive but also complicated because of the variability in both the type of debris and environmental conditions.

Pre-trained vision foundation models, such as DINOv2 (Oquab et al., 2024), CLIP (Radford et al., 2021), and OWL-ViT (Minderer et al., 2024), are promising solutions in this regard. These models are trained on large-scale and diverse image datasets, allowing them to learn generalized visual features. Such models can be fine-tuned for marine debris segmentation, even with limited data, by leveraging transferable visual knowledge.

## Creating scene-specific models
While large datasets are the norm in deep learning, they may not be the best approach for marine debris segmentation due to the diverse nature of debris and environmental conditions. A more targeted solution is to build region-specific models that focus on the unique characteristics of marine debris in specific locations. However, gathering enough data to train separate models for each region is impractical.

Instead of striving for generalizability, a more effective strategy might involve focusing on scene-specific segmentation. This approach is exemplified by the Personalize Segment Anything Model (PerSAM), which tailors its attention to local features, in this case the debris spectral signatures and the surrounding environment. By focusing on specific scenes, PerSAM could potentially reduce the need for large, diverse datasets.

## Overcoming PerSAM-F's limitations
One of the models I explored is PerSAM-F, an adaptation of SAM, which has shown great promise for one-shot segmentation tasks. However, applying this model directly to marine debris detection presented some challenges. Initial experiments revealed that PerSAM-F struggled with segmentation accuracy when applied to remote sensing data. To improve its performance, I made several modifications to the PerSAM-F architecture, specifically to better suit the task of marine debris segmentation.

PerSAM-F was originally designed to target single objects in an image. However, marine debris often consists of multiple, smaller objects, making it difficult for the model to segment them accurately. The original PerSAM-F model generates only two point prompts based on confidence maps, each focusing on a single object. This limitation makes it challenging to detect multiple objects in an image.

To address this issue, I introduced Farthest Point Sampling (FPS) into the model. FPS selects a subset of points that are well-separated from each other, reducing the likelihood of overlapping prompts. This modification enables the model to detect multiple objects in the same image, which is essential for marine debris segmentation, where the debris is often spread out and varied in size.

![](persam_prompts.png "Schematic of TopK Farthest Point Sampling (TopK-FPS) algorithm used for automated point prompt generation.")

## Comparative performance of marine debris models
To evaluate the improvements made to PerSAM-F, I compared its segmentation performance with other models, including SAM, Marine Debris Detector, and MariNeXt. The results, summarized in the table below, show that while the adapted PerSAM-F model shows promise, there are still challenges to overcome:

| Model                  | Automation | Accra F1 | Accra mIoU | Durban F1 | Durban mIoU |
|------------------------|------------|----------|------------|-----------|-------------|
| SAM                    | Low        | 53.8     | 36.8       | 54.4      | 38.0        |
| Adapted PerSAM-F       | Medium     | 24.2     | 13.8       | 22.0      | 12.4        |
| Marine Debris Detector | High       | 28.5     | 16.6       | 28.3      | 16.5        |
| MariNeXt               | High       | 50.5     | 33.7       | 20.6      | 11.4        |

As seen in the table, while the PerSAM-F model is on comparable performance to fully-trained globals, it still faces challenges, particularly when applied to datasets with high variability. The Accra dataset, for example, contains distinct patches of plastic debris and Sargassum, while the Durban dataset exhibits significant variation due to normalization techniques. These differences pose challenges for the model, which struggles to learn consistent visual representations of marine debris.

Additionally, the size of marine debris in remote sensing data, such as Sentinel-2 imagery, often results in small regions of interest that are difficult for the model to segment accurately. The PerSAM-F model, like SAM, is designed to segment larger target areas, which complicates the process of detecting small marine debris objects. The resulting location confidence maps are often noisy, and the generated point prompts can be misplaced, leading to incorrect segmentation predictions dominated by noise rather than actual debris.

![](persam_prompts.png "Visualization comparing manually annotated point prompts from the FloatingObjects dataset with automated points generated by the TopK-FPS algorithm in Durban, South Africa. PerSAM-F predictions focus on non-debris areas due to noisy location confidence maps, leading to misplaced prompts and inaccurate segmentation.")

## Future outlook
The performance difference between SAM and PerSAM-F on the marine debris datasets reveals the importance of prompt quality and quantity. Much of PerSAM-F's failure can be explained by the unreliable prompts from the TopK-FPS algorithm. This again roots in the noisy confidence maps, which do not segment the debris effectively from non-debris regions. To further improve the segmentation performance, the quality of the confidence maps needs to be improved.

Future research should therefore investigate the replacement of the image encoder in SAM with alternative deep feature extractors, pre-trained models optimized for remote sensing data to leverage Sentinel-2's full spectrum for better segmentation. Another direction is to fine-tune encoders of domain-specific models like Marine Debris Detector or MariNeXt to enhance overall performance by improving prompt generation. With these, the PerSAM-F can help marine scientists to solve their global problem of marine debris with an accessible, effective tool.