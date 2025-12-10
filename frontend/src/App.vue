<script setup>
import { onMounted } from 'vue'
import * as Cesium from 'cesium'

// 设置 Cesium 静态资源路径（必须）
window.CESIUM_BASE_URL = import.meta.env.VITE_CESIUM_BASE_URL

onMounted(async () => {
  const viewer = new Cesium.Viewer('cesiumContainer', {
    animation: false,
    timeline: false,
  })

  try {
    // Cesium 1.107+ 新版加载方式：使用 fromUrl 异步加载
    const tileset = await Cesium.Cesium3DTileset.fromUrl('/model/tileset.json')
    viewer.scene.primitives.add(tileset)
    
    // 飞向模型
    viewer.zoomTo(tileset)
  } catch (error) {
    console.error('3D Tiles 加载失败:', error)
  }
})
</script>

<template>
  <div id="cesiumContainer" style="width: 100vw; height: 100vh;"></div>
</template>

<style>
@import "cesium/Build/Cesium/Widgets/widgets.css";
</style>
