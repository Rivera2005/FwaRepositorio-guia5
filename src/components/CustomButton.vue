<template>
    <button :disabled="disabled" @click="$emit('click')" :class="{ 'disabled': disabled }">
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: 'CustomButton',
    props: {
        disabled: {
            type: Boolean,
            default: false
        }
    }
}
</script>

<style scoped>
button {
    padding: 10px 15px;
    margin: 0 10px;
    background-color: #2a2a2a;
    color: #39ff14;
    border: 2px solid #39ff14;
    border-radius: 5px;
    cursor: pointer;
    transition: all 0.3s ease;
}

button.disabled {
    background-color: #1a1a1a;
    border-color: #666;
    color: #666;
    cursor: not-allowed;
}

button:hover:not(.disabled) {
    background-color: #39ff14;
    color: #000;
}
</style>