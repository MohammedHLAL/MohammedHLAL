<!doctype html>
<html>
  <head>
    <title>WebMapping</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.5.0/css/ol.css" type="text/css"> 
    <script src="https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.5.0/build/ol.js"></script>
	
	
    <style type="text/css"> 
    html, body {
	height: 100%
	}
	#map {
        height: 100%;
        width: 100%;
      }
      h1{
        text-align: center;
        background: red;
        }
      </style>
  </head>
  <body>
    <h1>Afficher ma map ici...</h1>
    <div id="map"> </div>
    <script type="text/javascript">
      (function () {

        var view = new ol.View({
  projection:"EPSG:4326",
  center:[-7.69500, 33.53759 ],
  zoom:16
});
var map =new ol.Map({
  target:"map",
  view: view,
});

      var OSM = new ol.layer.Tile({
                        title: 'OSM',
                        type: 'base',
                        visible: true,
                        source: new ol.source.OSM(),
                    });

      var couche = new ol.layer.Image({
        title: "PARCELLES",
        source: new ol.source.ImageWMS({
          url: "http://localhost:8080/geoserver/wms",
          params: {"LAYERS": "WebgisHLAL:PARCELLES"},
          serverType: "geoserver"
        })
        });
        var couches = new ol.layer.Image({
        title: "PTECH",
        source: new ol.source.ImageWMS({
          url: "http://localhost:8080/geoserver/wms",
          params: {"LAYERS": "WebgisHLAL:PTECH"},
          serverType: "geoserver"
        })
      });
       map.addLayer(OSM);
      map.addLayer(couche);
      map.addLayer(couches);
})();
</script>
  </body>
</html>
