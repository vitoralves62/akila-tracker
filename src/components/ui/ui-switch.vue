<template>
    <div
        class="switch-wrapper"
        :class="{ 'is-disabled': disabled }"
        @click="toggle"
    >
        <span
            v-if="label"
            class="switch-label"
        >
            {{ label }}
        </span>

        <div
            class="switch-track"
            :class="{'is-active': modelValue}"
        >
            <div class="switch-thumb"></div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'ui-switch',

    props: {
        label: {
            type: String,
            default: ''
        },
        modelValue: {
            type: Boolean,
            default: false
        },
        disabled: {
            type: Boolean,
            default: false
        }
    },

    emits: ['update:modelValue'],

    methods: {
        toggle(){
            if(this.disabled) return;

            this.$emit('update:modelValue', !this.modelValue);
        }
    }
})
</script>

<style lang="css" scoped>

.switch-wrapper{
    display: inline-flex;
    align-items: center;
    cursor: pointer;
    gap: 10px;
    user-select: none;
}

.switch-wrapper.is-disabled{
    opacity: 0.6;
    cursor: not-allowed;
}

.switch-track{
    width: 50px;
    height: 26px;
    background-color: #ccc;
    border-radius: 20px;
    position: relative;
    transition: background-color 0.3s ease;
}

.switch-track.is-active {
    background-color: #94cde6; /* Verde */
}

.switch-thumb{
    width: 22px;
    height: 22px;
    background-color: #FFF;
    border-radius: 50%;
    position: absolute;
    top: 2px;
    left: 2px;
    transition: transform 0.3s ease;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.switch-track.is-active .switch-thumb{
    transform: translateX(24px);
}

.switch-label {
  font-family: sans-serif;
  font-size: 14px;
  color: #FFF;
}

</style>