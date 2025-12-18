<template>
    <section>
        <strong class="display">{{ realTime }}</strong>
    </section>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name:'ui-stopwatch',

        props: {
            time: {
                type: Number,
                default: 0
            }
        },

        computed:{
            realTime() : string {
                return new Date(this.time * 1000).toISOString().substring(11,19)
            }
        },
    })
</script>

<style lang="css" scoped>
    .display{
        color: var(--text-primary);
    }
</style>