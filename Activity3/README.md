<h1>Activity 3 - Use CitySDK to add Bernalillo County census block groups (neighborhoods) to the map</h1>
<h2>Intro:</h2>
In this activity, we’ll add census block groups (neighborhoods) and their poverty rates onto the map.


Every 10 years the US Census Bureau (UCSB) does a census survey.  They break up the country into blocks, block groups, census tracts, counties.  


Want to know more about census geographies? Google it.


After performing the census, USCB goes home and crunches a bunch of numbers and comes up with all these fun statistics, like poverty.  Historically, accessing this information has been really awful, but the UCSB recently released City SDK (Service Development Kit).  CitySDK is broken up into modules you can bring into your app and the modules are accessible on  <a href="https://github.com/uscensusbureau/citysdk">github</a>.  The modules we need have already been downloaded into the js folder.

Read more about <a href="http://uscensusbureau.github.io/citysdk/">getting started</a>.  To use CitySDK, you'll need an api key.   

Block groups for the entire county is a big dataset, so the dataset (geojson) was pre-downloaded for Bernalillo Coutnty.  It’s included in the “data folder.”  
 

<h3>Calculating poverty rate:</h3>
In this activity, we'll be calculating poverty rates by dividing the number of people living in poverty by the total population for each block group (units: number of people)


<h2>Getting to Work:</h2>

Just like you added the geojson layer to your map in the last activity, add the census block groups from file below it.

<ul>**Hint: add the following into your script.js file:</ul>

```
    var url = "../../data/census.geojson";
    $.ajax({
        url: url,
        dataType: 'json',
        success: function (data) {
            
            geojson = new L.GeoJSON(data, {
                
                onEachFeature: function(feature, layer){
                    layer.bindPopup("poverty: " + Math.floor(100*parseInt(feature.properties.poverty)/(feature.properties.population)) + "%");

                }
            });
            geojson.addTo(map);
            
        }

        
    });
```

<h3>Want to see the end product now?  Or are you stuck? </h3> Check out the FinishedCode folder for what your end product should look like.

<h2>Going further:</h2>
<ul><li>Interested in seeing CitySDK in action or want to send your own requests?  <a href="http://uscensusbureau.github.io/citysdk/guides/censusModule/aliases.html">Read</a> about other variables you can request and use the code in the 'alternate_citysdk_ajax _call.js' in this activity folder instead of the code above.  
<li>Try adding other variables to your popups

