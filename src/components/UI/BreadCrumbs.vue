<template>
    <div class="breadcrumbs">
        <!-- <img src="@/assets/images/icons/arrow.svg" alt=""> -->
        <div class="breadcrumbs__item" v-for="(crumb, index) in list">
            <div class="breadcrumbs__content">
                <p>{{ crumb.title }}</p>
                <p v-if="crumb.sum">{{ crumb.sum.toLocaleString('ru') }} предложения</p>
            </div>
            <div class="breadcrumbs__arrow" v-if="index !== list.length - 1">
                <img src="@/assets/images/icons/arrow.svg" alt="arrow/svg">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'BreadCrumbs',
    props: {
        list: { type: Array, default: [] }
    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";

.breadcrumbs {
    display: flex;
    flex-wrap: wrap;

    @include breakpoint(sm) {
        flex-direction: column;
    }

    &__item {
        margin-right: 40px;
        display: flex;
        margin-bottom: 20px;

        &:nth-last-child(1) {
            margin-right: 0;
        }

        @include breakpoint(md) {
            margin-right: 15px;
        }

        @include breakpoint(sm) {
            flex-direction: column;
            text-align: center;
            margin-right: 0;
        }
    }

    &__content {
        p {
            @include text($size: 12px, $weight: 400);

            @include breakpoint(md) {
                font-size: 10px;
            }

            &:nth-child(1) {
                color: #050F19;
                margin-bottom: 5px;

                @include breakpoint(md) {
                    margin-bottom: 0;
                }
            }

            &:nth-child(2) {
                color: #708598;
            }
        }
    }

    &__arrow {
        margin-left: 22px;
        @include flexcenter;

        @include breakpoint(sm) {
            margin-left: 0;
            margin-top: 10px;
        }

        img {
            transform: rotate(-90deg);

            @include breakpoint(sm) {
                transform: rotate(0deg);
            }
        }
    }
}
</style>