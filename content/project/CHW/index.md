---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "The Coastal Hazard Wheel Application"
summary: "Coastal classification through the Coastal Hazard Wheel"
authors: [admin]
tags: [Deltares, Geovisualization]
categories: []
date: 2021-09-01T17:33:42+02:00

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
One of the major projects I worked at during my internship at Deltares was for the Coastal Hazard Wheel ('CHW'). This is
a framework created by Lars Appelquist from the UN Environment Programme to “Manage coastal
challenges from local to global level”. The application can be used for classifying coastal locations worldwide and producing hazard maps for the hazards of ecosystem disruption, gradual inundation, salt water intrusion, erosion and flooding under the projected climate change.

Within this project, I assisted the team members through several tasks; 1) updating and acquire new datasets with frequently used sources as the USGS, UNEP-WCMC and OpenStreetMap. These were processed using Python and SQL (PostGIS). Afterwards, 2) I had to make sure that all data was uploaded into the correct database using PostgreSQL and PostGIS. At last, 3) I had to connect the database to GeoServer and create vizualisations of the data used. 

During this 7-month internship I learned quite a lot about creating webmaps, got my first introduction into programming  and experienced the usage of geo-information in a professional setting.

To view the results of my internship, check out the Coastal Hazard Wheel Application at chw20.netlify.com
