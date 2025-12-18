<template>
    <header>
        <h1>
            <img src="@/assets/logo.png" alt="" class="logo-image"/>
        </h1>
        <ui-switch
            :label="'Modo escuro:'"
            v-model="darkMode"
        />
    </header>
</template>

<script lang="ts">
    import uiSwitch from '@/components/ui/ui-switch.vue';
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'sidebar-main',

        components: {
            uiSwitch
        },

        data(){
            return{
                darkMode: false,
            }
        },

        emits: ['change-color-theme'],

        methods:{

        },

        watch: {
            darkMode(newValue: boolean) {
                this.$emit('change-color-theme', newValue);
            }
        }
    })
</script>

<style scoped>
header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
}
.logo-image{
    width: 200px !important; 
}
@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>