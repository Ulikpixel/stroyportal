<template>
    <div class="heroNavButtons">
        <button class="heroNavButtons__prev">
            <Arrow hoverColor="red" hover="red" />
        </button>
        <div class="heroNavButtons__wrapper">
            <div class="heroNavButtons__track">
                <button v-for="(btn, index) in list" :key="`${index}-${btn.title}`">{{ btn.title }}</button>
            </div>
        </div>
        <button class="heroNavButtons__next">
            <Arrow />
        </button>
    </div>
</template>

<script>
export default {
    props: {
        list: { type: Array, default: [] }
    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";

$border: #ECEFF1;

.heroNavButtons {
    height: 48px;
    border: solid 1px red;
    background: $bg;
    border: 1px solid $border;
    border-radius: 4px;
    margin-top: 21px;
    overflow: hidden;
    @include flexline;

    @include breakpoint(sm) {
        height: 30px;
    }

    button {
        background: none;
        border: none;
    }

    &__wrapper {
        width: 100%;
        overflow: hidden;
        height: 100%;
    }

    &__track {
        display: flex;
        align-items: center;
        height: 100%;

        button {
            border-right: solid 1px $border;
            height: 100%;
            cursor: pointer;
            padding: 12px 40px;
            white-space: nowrap;
            color: #050F19;
            @include text;

            &:nth-last-child(1) {
                border-right: 0;
            }

            @include breakpoint(sm) {
                font-size: 12px;
                padding: 6px 20px;
            }
        }
    }

    & &__prev,
    &__next {
        width: 48px;
        height: 48px;
        cursor: pointer;

        svg {
            path {
                fill: red !important;
            }
        }
    }

    & &__prev {
        border-right: 1px solid $border;

        svg {
            transform: rotate(90deg);
        }
    }

    & &__next {
        border-left: 1px solid $border;

        svg {
            transform: rotate(-90deg);
            &:hover {
                fill: red !important;
            }
        }
    }
}
</style>