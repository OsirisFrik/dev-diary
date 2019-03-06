---
title: Map marker transition
date: 'Wed, 6 Mar 2019 12:15:41 -0800'
stacks:
    - javascript
    - google
    - google maps
---

Read the blog to get stpes to make map marker transition

[How to Move Marker Smoothly on Google Map using JavaScript](https://www.codexworld.com/google-map-move-marker-smoothly-javascript-api/)

## Example
```javascript
var numDeltas = 100;
var delay = 10 //milliseconds
var i = 0
var deltaLat
var deltaLng

function transition(result){
    i = 0
    deltaLat = (result[0] - position[0])/numDeltas
    deltaLng = (result[1] - position[1])/numDeltas
    moveMarker()
}

function moveMarker(){
    position[0] += deltaLat
    position[1] += deltaLng
    var latlng = new google.maps.LatLng(position[0], position[1])
    if(i!=numDeltas){
        i++
        setTimeout(moveMarker, delay)
    }
}
```


