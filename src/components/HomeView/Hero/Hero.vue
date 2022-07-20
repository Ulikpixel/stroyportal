<template>
    <section class="hero">
        <div class="container">
            <div class="hero__breadcrumbs">
                <BreadCrumbs :list="breadcrumbs" />
            </div>
            <h1 class="hero__title">
                Штукатурка цементная цокольная Knauf Sockelpultz 25 кг
                <img src="@/assets/images/icons/share.svg" alt="share/icon">
            </h1>
            <NavButtons :list="categories" />
            <div class="hero__wrapper">
                <Product />
                <Advertising />
            </div>
        </div>
    </section>
</template>

<script>
import NavButtons from '@/components/HomeView/Hero/components/NavButtons';
import Product from '@/components/HomeView/Hero/components/Product';
import Advertising from '@/components/HomeView/Hero/components/Advertising';

export default {
    data() {
        return {
            breadcrumbs: [
                { title: 'Каталог', sum: 4442512 },
                { title: 'Строительные материалы ', sum: 4442512 },
                { title: 'Сухие строительные смеси ', sum: 4442512 },
                { title: 'Шпатлевки ', sum: 4442512 },
                { title: 'Шпатлевка Knauf', sum: null },
            ],
            categories: [
                { title: 'Где купить', link: '' },
                { title: 'Описание', link: '' },
                { title: 'Характеристики', link: '' },
                { title: 'Динамика цен', link: '' },
                { title: 'Календарь низких цен', link: '' },
                { title: 'Сравнение', link: '' },
                { title: 'Корзина', link: '' },
            ]
        }
    },
    components: { NavButtons, Product, Advertising }
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";

.hero {
    background: $bg;
    padding: 16px 0 87px;

    &__title {
        @include text($weight: 700, $size: 28px);

        @include breakpoint(md) {
            font-size: 20px;
            text-align: center;
        }

        @include breakpoint(xs) {
            font-size: 16px;
        }

        img {
            width: 20px;
            height: 20px;
            margin-left: 4px;
        }
    }
    &__wrapper {
        margin-top: 30px;
        display: flex;
        justify-content: space-between;
        @include breakpoint(lg) {
            flex-direction: column;
            align-items: center;
        }
    }
}
</style>