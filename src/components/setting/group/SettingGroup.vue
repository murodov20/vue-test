<script setup>
import {defineProps} from 'vue'

defineProps(['setting', 'depth'])

</script>
<template>
    <div :style="{'margin-left': (depth * 5) + 'px'}">
        group>
    </div><slot />
</template>