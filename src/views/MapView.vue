<template>
  <div id="MapView" class="flex flex-col h-screen">
    <div id="map" style="width: 100%; height: 100%"></div>
  </div>
</template>

<script setup>
import { onMounted } from "vue";
import L from "leaflet";

const initMap = () => {
  const map = L.map("map").setView([51.505, -0.09], 13);

  L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
    attribution:
      '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
  }).addTo(map);

  console.log(map);
};

onMounted(() => {
  const script = document.createElement("script");
  script.src = `https://cdn.jsdelivr.net/npm/leaflet/dist/leaflet.js`;
  script.async = true;
  script.onload = () => {
    console.log("Leaflet đã sẵn sàng.");
    initMap();
  };
  script.onerror = () => {
    console.error("Lỗi khi tải thư viện Leaflet.");
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
