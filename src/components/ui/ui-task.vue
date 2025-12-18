<template>
    <box-template>
        <div class="columns">
            <div class="column is-7">
                {{ task.description || 'Tarefa sem descrição.'}}
            </div>
            <div class="column">
                <ui-stopwatch
                    :time="task.time"
                />
            </div>
        </div>
    </box-template>
</template>

<script lang="ts">
    import { defineComponent, PropType } from 'vue';

    import boxTemplate from '@/templates/box-template.vue';
    import uiStopwatch from '@/components/ui/ui-stopwatch.vue';
    import ITask from '@/interfaces/ITask';

    export default defineComponent({
        name: 'ui-task',

        components: {
            uiStopwatch,
            boxTemplate
        },

        props: {
            task: {
                type: Object as PropType<ITask>,
                required: true
            }
        }
    })
</script>

<style lang="css" scoped>
    
</style>