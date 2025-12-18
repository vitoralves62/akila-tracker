<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <ui-stopwatch
            :time="currentTime"
        />
        <ui-button
            :clickAction="startCount"
            :isDisabled="isCounting"
            :icon="'fas fa-play'"
            :text="'play'"
        />
        <ui-button
            :clickAction="endCount"
            :isDisabled="!isCounting"
            :icon="'fas fa-stop'"
            :text="'stop'"
        />
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    import UiStopwatch from '@/components/ui/ui-stopwatch.vue';
    import uiButton from '../ui/ui-button.vue';

    export default defineComponent({
        name:'main-timer',

        components: {
            UiStopwatch,
            uiButton,
        },

        data() {
            return{
                currentTime: 0,
                stopwatch: 0,
                isCounting: false,
            }
        },

        emits: ['timerIsStoped'],

        methods:{
            startCount(){
                this.isCounting = true;
                this.stopwatch = setInterval(() =>{
                    this.currentTime += 1;
                }, 1000)
            },
            endCount(){
                clearInterval(this.stopwatch);
                this.isCounting = false;
                this.$emit('timerIsStoped', this.currentTime);
                this.currentTime = 0;
            },
        }
    })
</script>