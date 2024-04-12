# How would you add another class to your choropleth map?
To add another class to the map is to add another paired category to the getColor() function. For example, in this function:
```
function getColor(value) {
 return value > 50000000 ? '#54278f':
        value > 25000000 ? '#756bb1': 
        value > 10000000 ? '#9e9ac8': 
        value > 5000000 ? '#cbc9e2';
  }
```
Adding one more pair will be:
```
function getColor(value) {
 return value > 50000000 ? '#54278f':
        value > 25000000 ? '#756bb1': 
        value > 10000000 ? '#9e9ac8': 
        value > 5000000 ? '#cbc9e2':
        value > 2500000 ? '#f2f0f7';
  }
```
There will be a new data range (here `value > 2500000`, with its respective color assigned. One may also adjust the color (e.g., in a gradient manner) as per needs. 
# How might you create a map where all overlay layers are toggled OFF by default? Why might this be a useful option?

To create a map where all overlay layers are toggled off, i.e., overlays will not automatially show when load the may for the first time and need to be turned on manually, one have to make sure the overlay layer is not added to the map directly when defining it. Using the case in the lab 2 assignment, 
```
var provinces = L.geoJson(provinces, {style:style}).addTo(map);
var basemaps = {
            "Terrain": canvas,
            "Satellite": imagery
        };
        var overlaymaps = {
            "China Provinces": provinces
        };
L.control.layers(basemaps, overlaymaps, {collapsed:false}).addTo(map);
```
here it is automatically toggled on because there is `.addTo(map)` when defining the provinces variable. One have to delete it and only keep `.addTo(map)` in the Leaflet control function, as shown on the last line of code. 
