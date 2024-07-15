<template>
  <div class="flex justify-center items-center h-screen">
    <div class="w-[900px] aspect-square bg-checkerboard">
      <TresCanvas>
        <TresOrthographicCamera
          :args="[-1, 1, 1, -1, 0, 10]"
          :position="[0, 0, 0]"
        />
        <TresMesh ref="mesh">
          <TresPlaneGeometry :args="[2, 2]" />
          <TresShaderMaterial
            :vertex-shader="vertexShader"
            :fragment-shader="fragmentShader"
          />
        </TresMesh>
      </TresCanvas>
    </div>
  </div>
</template>

<script setup lang="ts">
import vertexShader from '@/assets/shaders/vertex.glsl'
import fragmentShader from '@/assets/shaders/fragment.glsl'
</script>

<style scoped lang="postcss">
.bg-checkerboard {
  --checkerboard-size: 20px;
  --checkerboard-colour: rgba(0, 0, 0, 0.03);

  background-image: linear-gradient(
      45deg,
      var(--checkerboard-colour) 25%,
      transparent 25%,
      transparent 75%,
      var(--checkerboard-colour) 75%,
      var(--checkerboard-colour)
    ),
    linear-gradient(
      45deg,
      var(--checkerboard-colour) 25%,
      transparent 25%,
      transparent 75%,
      var(--checkerboard-colour) 75%,
      var(--checkerboard-colour)
    );
  background-position:
    0 0,
    calc(var(--checkerboard-size) / 2) calc(var(--checkerboard-size) / 2);
  background-size: var(--checkerboard-size) var(--checkerboard-size);
}
</style>
