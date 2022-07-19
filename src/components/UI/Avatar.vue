<template>
    <div class="avatar" :style="{ background: color || currentColor }">
        <p>{{ fullname.slice(0, 1) }}</p>
    </div>
</template>

<script>
export default {
    name: 'Avatar',
    data() {
        return {
            currentColor: 'pink',
        }
    },
    props: {
        fullname: { type: String, required: true },
        color: { type: String, default: null }
    },
    mounted() {
        const colors = ['red', 'yellow', 'green', 'blue', 'black', 'gray', 'pink'];
        const random = colors[Math.floor(Math.random()*colors.length)];
        this.currentColor = random;
    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";

.avatar {
    width: 40px;
    height: 40px;
    background: red;
    border-radius: 50%;
    cursor: pointer;
    @include flexcenter;

    p {
        @include text($weight: 600);
        color: white;
    }
}
</style>