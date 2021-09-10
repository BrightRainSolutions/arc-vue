<template>
  <div id="map"></div>
</template>

<script>
import Map from "@arcgis/core/WebMap";
import MapView from "@arcgis/core/views/MapView";
import FeatureLayer from "@arcgis/core/layers/FeatureLayer";
import Legend from "@arcgis/core/widgets/Legend";

export default {
  name: 'ArcMap',
  props: {
    theMap: Object
  },
  mounted() {
    this.map = new Map({
      //basemap: "topo-vector"
      basemap: "dark-gray-vector"
    });

    this.view = new MapView({
      map: this.map,
      container: 'map',
      center: [-120, 34],
      zoom: 6
    });
    // https://www.arcgis.com/home/item.html?id=d257743c055e4206bd8a0f2d14af69fe
    const url = "https://services2.arcgis.com/FiaPA4ga0iQKduv3/arcgis/rest/services/Colleges_and_Universities_View/FeatureServer";
    const colleges = new FeatureLayer(url, {
      outFields: ["NAME","TOT_ENROLL"],
      popupTemplate: {
      "title": "{NAME}",
      "content": "<b>Enrollment: {TOT_ENROLL}</b>"
      }
    });
    this.map.add(colleges);

    this.view.ui.add(new Legend({ view: this.view }), "bottom-left");
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://js.arcgis.com/4.20/@arcgis/core/assets/esri/themes/dark/main.css";
#map {
  height: 100%;
  width: 100%;
  margin: 0
}
</style>
