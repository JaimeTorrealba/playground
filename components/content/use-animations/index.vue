<script setup lang="ts">
import { TresCanvas } from '@tresjs/core'
import { BasicShadowMap, sRGBEncoding, NoToneMapping } from 'three'

import { OrbitControls } from '@tresjs/cientos'
import UglyNakedBunny from './UglyNakedBunny.vue'

const gl = {
  clearColor: '#F78B3D',
  shadows: true,
  alpha: false,
  shadowMapType: BasicShadowMap,
  outputEncoding: sRGBEncoding,
  toneMapping: NoToneMapping,
}
</script>

<template>
  <TresCanvas v-bind="gl">
    <TresPerspectiveCamera :position="[2, 3, 8]" :look-at="[0, 0, 0]" />
    <OrbitControls />
    <TresDirectionalLight color="#F78B3D" :position="[3, 3, 3]" :intensity="1" />
    <Suspense>
      <UglyNakedBunny />
    </Suspense>
    <TresAmbientLight :intensity="2" />
  </TresCanvas>
</template>
