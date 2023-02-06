---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Identifying oxbow lakes from satellite data"
summary: "Using SAR for distinguishing different water types ins western New Guinea"
authors: [admin]
tags: [Wageningen UR, programming, geovisualization]
categories: []
date: 2023-02-03T15:30:57+02:00

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
TL;DR
- We identified oxbow lakes from Sentinel-1 (SAR) and auxillary data from the [Global Surface Water Explorer](https://global-surface-water.appspot.com/download)
- {{< staticref "uploads/oxbowlakes-interactiveMap.html" "newtab" >}} Interactive map of the oxbow lakes in western New Guinea{{< /staticref >}}
-	[Source code on Github](https://github.com/geoJoost/oxbow-lake-detection)

For the course Geoscripting at Wageningen University & Research, we learned to do process geospatial data using R, Python, bash and Google Earth Engine. In the final week, we had the opportunity to integrate all that knowledge in a single project. Together with my group members[^1], we created an algorithm that can distinguish oxbow lakes from Sentinel-1 synthetic aperture radar (SAR) imagery.

For the (many) who are not aware what an oxbow lake is; they are crucial freshwater wetland ecosystems that are formed when the neck of a meandering river is breached. Over time the old meander of the river will be disconnected from the main channel through sediment deposition, like depicted below[^2].

![](figure_oxbowlakes-formation.png "Simplified sketch on formation of oxbow lakes")
 
When visualized using a time series of satellite imagery, the effect becomes even more pronounced as [seen in our study area of western New Guinea](https://earthengine.google.com/timelapse#v=-3.31616,139.0256,10.624,latLng&t=0.35&ps=25&bt=19840101&et=20201231&startDwell=0&endDwell=0)

In brief, the following method was used:
![](figure_oxbowlakes-method.png "Method used to detect oxbow lakes from SAR data")
 
Which lead to the following results: 
- Interactive map through Leaflet
- Dynamic map (GIF)
- Static map

First, was the interactive map of the area where the user can pan and zoom to their desired location. The Leaflet map also allows users to select the year of their choice while also having the option to (de-)select the showing of ‘normal’ or oxbow lakes. {{< staticref "uploads/oxbowlakes-interactiveMap.html" "newtab" >}}Test it yourself with this link!{{< /staticref >}}

![](figure_oxbowlakes-html.png "Screenshot of the interactive map in Leaflet")

The second visualization created was a GIF of the entire time series. This would allow users to see if certain lakes grew or shrink during the entire period, however, due to processing limits we only selected a few images which limits the application of this method. 

![](figure_oxbowlakes-gif.gif "Dynamic map of selected images from 2015-2023")

The last method is a static map of all the water features found within the study area. Through a Bash script users were prompted to select a year of their choice which would output an image like seen below. This was my first time creating an inset map through scripting which was a challenge to implement but eventually led to some good-looking results.

![](figure_oxbowlakes-static2019.png "Static map of the water features in western New Guinea [2019]")

The past four days were intense but were rewarding. In a short amount of time, we managed to write an algorithm that is reasonably good at identifying oxbow lakes from SAR data. Personally, I improved a lot in my scripting abilities (both R and Python) while also learning how to use Bash.

Feel free to download and re-use the [code available on Github!](https://github.com/geoJoost/oxbow-lake-detection)


[^1]:*With Isaura Menezes de Oliveira Guido, Isabeau Verbrugge, Wessel van Leesten & Nikolas Theofanous*
[^2]: Image sourced from [Internet Geography](https://www.internetgeography.net/flashcard/draw-a-simple-diagram-to-show-the-formation-of-an-oxbow-lake/)
