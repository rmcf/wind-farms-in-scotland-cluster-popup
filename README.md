# Wind farms in Scotland

### circleMarker popup fixed

![Screenshot from 2024-02-03 15-10-11](https://github.com/rmcf/wind-farms-in-scotland-cluster-popup/assets/18697688/b4a11fe0-c457-46e2-8262-e27c77bd7496)

Original repository: https://github.com/majaturkalj/wind-farms-in-scotland

Added this code to the script section into `index.html` to make popups work with clustering plugin

```JS
      // clustering with popups
      // ==========================================================
      var markers = L.markerClusterGroup()

      L.geoJSON(windFarmsAll, {
        pointToLayer: function (feature, latlng) {
          return L.circleMarker(latlng, markerStyle(feature))
        },
        onEachFeature: function (feature, layer) {
          layer.bindPopup(markerPopUp(feature))
        },
      }).addTo(markers)

      map.addLayer(markers)

      // circle style
      function markerStyle(feature) {
        return {
          radius: 5,
          color: feature.properties.color,
          weight: 1,
          opacity: 1,
          fillOpacity: 0.9,
        }
      }

      // circle popup content
      function markerPopUp(feature) {
        const text =
          '<h4>Wind Farms</h4>' +
          '<div class="container"><table class="table table-striped">' +
          '<tbody><tr><td> Name </td><td>' +
          feature.properties.Name +
          '</td></tr>' +
          '<tr><td>Type </td><td>' +
          feature.properties.Type +
          '</td></tr>' +
          '<tr><td> Capacity (MW) </td><td>' +
          feature.properties.MW
        return text
      }
      // ==========================================================

```
