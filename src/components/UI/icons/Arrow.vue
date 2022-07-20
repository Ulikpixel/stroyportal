<template>
    <svg width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M0.5 0.75L5 5.25L9.5 0.75" :stroke="color" stroke-linecap="round" stroke-linejoin="round" />
    </svg>
</template>

<script>
export default {
    name: 'Arrow',
    props: {
        color: { type: String, default: '#708598' }
    }
}
</script>