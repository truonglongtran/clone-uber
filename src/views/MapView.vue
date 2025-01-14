<template>
  <div id="MapView" class="flex flex-col h-screen">
    <div id="map" style="width: 100%; height: 100%"></div>
  </div>
</template>

<script setup>
import { onMounted } from "vue";

const initMap = () => {
  if (!window.google || !window.google.maps) {
    console.error("Google Maps API chưa được tải.");
    return;
  }

  const map = new window.google.maps.Map(document.getElementById("map"), {
    center: { lat: -34.397, lng: 150.644 },
    zoom: 8,
  });
  console.log(map);
};

onMounted(() => {
  const script = document.createElement("script");
  script.src = `https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY`;
  script.async = true;
  script.defer = true;
  script.onload = () => {
    console.log("Google Maps API đã sẵn sàng.");
    initMap();
  };
  script.onerror = () => {
    console.error("Lỗi khi tải Google Maps API.");
  };
  document.head.appendChild(script);
});
</script>

<style lang="scss" scoped>
#map {
  width: 100%;
  height: 100%;
}
</style>
..........
