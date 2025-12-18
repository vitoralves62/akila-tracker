<template>
    <div class="box hax-text-weight-bold">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: 'box-template'
})

</script>

<style lang="css" scoped>
    .box{
        background-color: #f0f898;
    }
</style>