<template>
    <div class="catalog">
        <button class="hamburger hamburger--collapse" type="button"
            @click="active = !active">
            <span class="hamburger-box">
                <span class="hamburger-inner"></span>
            </span>
        </button>
        <p>Каталог</p>
        <ul :class="active ? 'catalog__content active' : 'catalog__content'">
            <li>1 element</li>
            <li>2 element</li>
            <li>3 element</li>
            <li>4 element</li>
            <li>5 element</li>
        </ul>
    </div>
</template>

<script>
export default {
    data() {
        return {
            active: false
        }
    }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/index.scss';

.catalog {
    width: 116px;
    min-height: 40px;
    background: $orange;
    border-radius: 4px;
    position: relative;
    @include flexline;
    justify-content: center;

    p {
        margin-left: 10px;
        font-weight: 600;
        font-size: 14px;
        font-family: $opensans;
    }

    .hamburger {
        width: 20px;
        height: 20px;
        padding: 0;
        margin: 0;

        &-box {
            width: 20px;
            height: 20px;
        }

        &-inner,
        &-inner:after,
        &-inner:before {
            width: 20px;
            height: 2px;
        }

        &-inner {
            top: 5px;
        }

        &-inner:after {
            top: 5px;
        }

        &-inner:before {
            top: 10px;
        }
    }

    &__content {
        position: absolute;
        width: 100%;
        top: 95%;
        left: 0;
        background: $orange;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        max-height: 0;
        transition: max-height 0.15s ease-out;
        overflow: hidden;
        text-align: center;
        z-index: 1;

        li {
            margin: 0 5px 10px;
            font-family: $opensans;
            font-size: 12px;

            &:nth-last-child(1) {
                margin-bottom: 0;
            }
        }

        &.active {
            max-height: 500px;
            transition: max-height 0.25s ease-in;
            padding-bottom: 10px;
        }
    }
}
</style>