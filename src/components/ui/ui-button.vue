<template>
    <button class="button" @click="clickAction" :disabled="isDisabled">
        <span class="icon">
            <i :class="icon"></i>
        </span>
        <span>{{ text }}</span>
    </button>
</template>

<script lang="ts">
    import { defineComponent, PropType } from 'vue';

    export default defineComponent({
        name: 'ui-button',

        props: {
            clickAction:{
                type: Function as PropType<() => void>,
                default: () => {/**void */}
            },
            isDisabled: {
                type: Boolean,
                default: false
            },
            icon:{
                type: String,
                default: ''
            },
            text:{
                type: String,
                default: ''
            }
        }
    })
</script>