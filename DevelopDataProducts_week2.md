---
title: "Developing Data Products - Project week 2"
author: "Elisa Battistoni"
output: 
  html_document: 
    keep_md: yes
---

This is a webpage created with R Markdown that features a map created with Leaflet.
This webpage is hosted on GitHub Pages.

Date and time of document creation:

```r
date()
```

```
[1] "Wed Aug 22 14:26:47 2018"
```

Interactive map created with Leaflet:

```r
library(leaflet)

MyLeafletLatLong = data.frame(
    lat = c(41.543924, 40.514680, 46.44548, 48.1351),
    long = c(12.285448, 14.163612, 11.74872, 11.5820)
)

Rome_Icon = makeIcon(
    iconUrl = "https://www.informagiovani-italia.com/colosseo1.jpg",
    iconWidth = 31*215/230, iconHeight = 31,
    iconAnchorX = 31*215/230/2, iconAnchorY = 16
)

Trento_Icon = makeIcon(
    iconUrl = "http://archivio.lavocedeltrentino.it/wp-content/uploads/2016/07/orso-buno-con-cuccioli-900x450.jpg",
    iconWidth = 31*215/230, iconHeight = 31,
    iconAnchorX = 31*215/230/2, iconAnchorY = 16
)

Napoli_Icon = makeIcon(
    iconUrl = "http://2.citynews-napolitoday.stgy.ovh/~media/original-hi/59187489013853/pizza-14-13.jpg",
    iconWidth = 31*215/230, iconHeight = 31,
    iconAnchorX = 31*215/230/2, iconAnchorY = 16
)

Munich_Icon = makeIcon(
    iconUrl = "https://cdn.images.dailystar.co.uk/dynamic/162/photos/578000/620x/oktoberfest-549933.jpg",
    iconWidth = 31*215/230, iconHeight = 31,
    iconAnchorX = 31*215/230/2, iconAnchorY = 16
)

MyLeafletLatLong %>% 
    leaflet() %>%
    addTiles() %>%
    addMarkers(lat=41.543924, lng=12.285448, popup="Roma", icon = Rome_Icon) %>%
    addMarkers(lat=40.514680, lng=14.163612, popup="Napoli", icon = Napoli_Icon) %>%
    addMarkers(lat=46.44548, lng=11.74872, popup="Trento", icon = Trento_Icon) %>%
    addMarkers(lat=48.1351, lng=11.5820, popup="München", icon = Munich_Icon)
```

<!--html_preserve--><div id="htmlwidget-30dd49ae70f53048e372" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-30dd49ae70f53048e372">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addMarkers","args":[41.543924,12.285448,{"iconUrl":{"data":"https://www.informagiovani-italia.com/colosseo1.jpg","index":0},"iconWidth":28.9782608695652,"iconHeight":31,"iconAnchorX":14.4891304347826,"iconAnchorY":16},null,null,{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},"Roma",null,null,null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]},{"method":"addMarkers","args":[40.51468,14.163612,{"iconUrl":{"data":"http://2.citynews-napolitoday.stgy.ovh/~media/original-hi/59187489013853/pizza-14-13.jpg","index":0},"iconWidth":28.9782608695652,"iconHeight":31,"iconAnchorX":14.4891304347826,"iconAnchorY":16},null,null,{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},"Napoli",null,null,null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]},{"method":"addMarkers","args":[46.44548,11.74872,{"iconUrl":{"data":"http://archivio.lavocedeltrentino.it/wp-content/uploads/2016/07/orso-buno-con-cuccioli-900x450.jpg","index":0},"iconWidth":28.9782608695652,"iconHeight":31,"iconAnchorX":14.4891304347826,"iconAnchorY":16},null,null,{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},"Trento",null,null,null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]},{"method":"addMarkers","args":[48.1351,11.582,{"iconUrl":{"data":"https://cdn.images.dailystar.co.uk/dynamic/162/photos/578000/620x/oktoberfest-549933.jpg","index":0},"iconWidth":28.9782608695652,"iconHeight":31,"iconAnchorX":14.4891304347826,"iconAnchorY":16},null,null,{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},"München",null,null,null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]}],"limits":{"lat":[40.51468,48.1351],"lng":[11.582,14.163612]}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->

