---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "The Sinking Soils of Amstel, Gooi & Vecht"
summary: "Soil subsidence in the water board of Amstel, Gooi and Vecht"
authors: [admin]
tags: [Wageningen UR, programming, geovizulasiation]
categories: []
date: 2022-10-03T22:15:57+02:00

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
The first project after starting the MSc Geo-Information Science was to develop a StoryMap based on a environmental topic in your country. As we had The Netherlands, we chose the topic: “The Sinking Soils of Amstel, Gooi & Vecht”. In approximately a week we (Lena Sakalak, Juriaan Rijsdijk, Ilse Radix, Francesco Pasanisi, Liam Adam, and I) developed and researched the issue of soil subsidence in the region of the water board.

Together we de developed a cohesive story surrounding the issue with maps (e.g., land use, soil types) and pictograms. In the meanwhile, Francesco Pasanisi and I developed a script to analyze soil subsidence using the AHN data (Algemeen Hoogtebestand Nederland; national DEM of The Netherlands).
![](figure_AHN_timeline.png "Timeline of AHN measurements")

Substracting each dataset with the previous version allowed us to get a rate of subsidence, and the total subsidence throughout the area. This data was joined to building footprints to allow homeowners to get actual insight on the potential sinking of their house since 1997.

![](figure_AHN_method.png "Methodology used to calculate the soil subsidence")

[The final results, and the Esri StoryMap can be seen here.](https://storymaps.arcgis.com/stories/97847336d2db453a98dffc7bf87770f2)

![](figure_AHN_results.png "Final results from the calculations for Amstel, Gooi & Vecht")

Note that this was more of an experiment as more reliable methods are available through the usage of InSAR as can be seen by the [Bodemdalingskaart 2.0 as developed by SkyGeo](https://bodemdalingskaart.portal.skygeo.com/portal/bodemdalingskaart/u2/viewers/basic/)

