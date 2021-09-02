---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Terrain dependency of deforestation in Borneo"
summary: "Research into the relationship between deforestation and slope/elevation"
authors: []
tags: [Wageningen UR, programming]
categories: []
date: 2021-07-02T22:15:57+02:00

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
During my minor (see “CV”) at Wageningen University & Research, I had the opportunity to conduct independent research using spatial data. In this period, I researched the relationship between deforestation and two terrain parameters (slope and elevation) on the island of Borneo. The final report was aptly titled “Assessing terrain dependency of deforestation in Borneo (2001-2019)”.

The aim of this research was to gain more insight in the terrain dependency of deforestation as it is was hypothesized that deforestation in the last two decades (2001-2019) has increased on less accessible terrain on the island of Borneo. Using data from the Global Forest Watch and from the Shuttle Radar Topography Mission, I was able to categorize deforestation in four categories using slope (derived from SRTM) and elevation data.

Afterwards the relative deforestation was calculated by summing up all deforestation
pixels in a single year per terrain category and dividing this value by the total of all
deforestation pixels in that year. At last, a simple regression was calculated leading to the two figures below.

![](figure_Slope_graph.png "Graphs indicating relative deforestation within different slope classes between the period of 2001-2019")
![](figure_Elevation_graph.png "Graphs indicating relative deforestation within different elevation classes between the period of 2001-2019")

As can be seen in the figures, most of the conversion to non-forest state has occurred in the defined lowland classes, slope lower than 10% and elevation below 500 meters, with each category containing 84% and 95% of total area deforested. In addition, once a simple regression had been calculated, a negative trend was detected along the aforementioned lowland classes, meaning that deforestation has been decreasing in comparison with the other categories. On the other hand, a positive trend was established in the second and third categories where deforestation has been gradually increasing. Therefore, the relationship between the terrain parameters and deforestation
indicate that extensive clearing of lowland forests causes a drive towards less accessible
terrain.

This project was extremely interesting but challenging. It was the first time I created an entire script in Python from scratch which lead to quite interesting results. For more detailed information and analysis, {{% staticref "uploads/TerrainDependencyOfDeforestationInBorneo_JvanDalen.pdf" "newtab" %}} the report is available online{{% /staticref %}}


