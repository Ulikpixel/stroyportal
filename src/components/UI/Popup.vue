<template>
    <div :class="active ? 'popup active' : 'popup'"></div>
</template>

<script>
    export default {
        name: 'Popup',
        props: {
            active: { type: Boolean, default: false }
        }
    }
</script>

<style lang="scss" scoped>
    .popup {
        position: fixed;
        left: 0;
        top: 0;
        height: 100%;
        width: 100%;
        z-index: 80;
        background: rgba(5, 15, 25, 0.3);
        cursor: pointer;
        display: none;
        &.active {
            display: block;
        }
    }
</style>