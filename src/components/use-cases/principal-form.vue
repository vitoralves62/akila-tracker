<template>
    <div class="box principal-form">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de tarefas">
                <input 
                    type="text" 
                    class="input" 
                    placeholder="Qual tarefa você deseja inciar?"
                    v-model="taskDescription"
                />
            </div>
            <div class="column">
                <main-timer
                    @timer-is-stoped="finishTask"
                />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    import mainTimer from '@/components/use-cases/main-timer.vue';

    export default defineComponent({
        name:'principal-form',

        components: {
            mainTimer
        },

        emits: ['add-task'],

        data() {
            return{
                taskDescription: '',
            }
        },

        methods:{
            finishTask(currentTime: number) : void{
                this.$emit('add-task', {
                    time: currentTime,
                    description: this.taskDescription
                })
                this.taskDescription = '';
            }
        }
    })
</script>

<style>
.principal-form{
    color: var(--text-primary);
    background-color: var(--bg-primary);
}
</style>