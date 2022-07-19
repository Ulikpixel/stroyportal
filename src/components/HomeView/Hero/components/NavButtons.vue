<template>
    <div class="navButtons">
        <button class="navButtons__prev">
            <img src="@/assets/images/icons/arrow.svg" alt="arrow/icon">
        </button>
        <div class="navButtons__wrapper">
            <div class="navButtons__track">
                <button v-for="(btn, index) in list" :key="`${index}-${btn.title}`">{{ btn.title }}</button>
            </div>
        </div>
        <button class="navButtons__next">
            <img src="@/assets/images/icons/arrow.svg" alt="arrow/icon">
            <!-- <Arrow /> -->
        </button>
    </div>
</template>

<script>
import Arrow from "@/assets/images/icons/arrow.svg";

export default {
    props: {
        list: { type: Array, default: [] }
    },
    components: {
        Arrow
    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";

$border: #ECEFF1;

.navButtons {
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
    }

    & &__prev {
        border-right: 1px solid $border;
        img {
            transform: rotate(90deg);
        }
    }

    & &__next {
        border-left: 1px solid $border;
        img {
            transform: rotate(-90deg);
        }
    }
}
</style>