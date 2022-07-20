<template>
    <div class="heroProduct">
        <div class="heroProductCart">
            <div class="heroProductCart__block">
                <div class="heroProductCart__advertising">
                    <button>Хит продаж</button>
                    <button>
                        Акция
                    </button>
                </div>
                <button class="heroProductCart__list">
                    <img src="@/assets/images/icons/plus.svg" alt="plus/icon">
                    В список
                </button>
                <img :src="product.img" alt="img" class="heroProductCart__image">
                <p>Наведите на изображение, чтобы увеличить его</p>
            </div>
            <div class="heroProductCartSlider">
                <Arrow @click="arrowClick('next')" />
                <div class="heroProductCartSlider__wrapper">
                    <div class="heroProductCartSlider__track">
                        <div @click="changeProduct(item.id)"
                            :class="product.id === item.id ? 'heroProductCartSlider__item active' : 'heroProductCartSlider__item'"
                            v-for="(item, index) in list" :key="`${index}-${item.name}`">
                            <img :src="item.img" alt="img">
                        </div>
                    </div>
                </div>
                <Arrow @click="arrowClick('prev')" />
            </div>
        </div>
        <div class="heroProductContent">
            <div class="heroProductContentBox heroProductContentBox__info">
                <img src="@/assets/images/icons/file-text.svg" alt="file/text">
                <div class="heroProductContentBox__content">
                    <p class="heroProductContentBox__title">Коротко о товаре</p>
                    <p>Вес · <span>{{ product.weight[0] }} - {{ product.weight[1] }} кг</span></p>
                    <p>Основа · <span>{{ product.name }}</span></p>
                    <a href="">Все характеристики</a>
                </div>
            </div>
            <div class="heroProductContentBox heroProductContentBox__views">
                <img src="@/assets/images/icons/thumbs-up.svg" alt="thumbs/up">
                <div class="heroProductContentBox__content">
                    <p class="heroProductContentBox__title">Пользуется спросом</p>
                    <div>
                        <p>{{ product.view }} просмотров</p>
                        <p>{{ product.refusal }} заказа</p>
                    </div>
                </div>
            </div>
            <div class="heroProductContentBox heroProductContentBox__offer">
                <img src="@/assets/images/icons/check-circle.svg" alt="check/circle">
                <div class="heroProductContentBox__content">
                    <p class="heroProductContentBox__title">В наличии в Москве на 4 марта 2020</p>
                    <a href="">{{ product.offer }} предложений</a>
                </div>
            </div>
            <div class="heroProductContentBox__logo">
                <img src="@/assets/images/knauf.png" class="heroProductContent__logo" alt="image/logo">
            </div>
        </div>
    </div>
</template>

<script>
const list = [
    {
        id: 1,
        weight: [25, 50],
        name: 'Гипсовая супер штукатурка Knauf S...',
        view: 2274,
        refusal: 602,
        offer: 140,
        img: require('@/assets/images/slider-1.png')
    },
    {
        id: 2,
        weight: [11, 90],
        name: 'Название товара номер 2',
        view: 101,
        refusal: 2,
        offer: 10,
        img: require('@/assets/images/slider-2.png')
    },
    {
        id: 3,
        weight: [20, 50],
        name: 'Название товара номер 3',
        view: 123,
        refusal: 4,
        offer: 0,
        img: require('@/assets/images/slider-3.png')
    },
];

export default {
    data() {
        return {
            list: [],
            product: list[0]
        }
    },
    methods: {
        changeProduct(id) {
            const product = list.find(el => el.id === id);
            this.product = product;
        },
        arrowClick(type) {
            if (type === 'next') {
                const idx = list.findIndex(el => el.id === this.product.id);
                const next = idx === list.length - 1 ? 0 : idx + 1;
                this.product = list[next];
            }
            if (type === 'prev') {
                const idx = list.findIndex(el => el.id === this.product.id);
                const prev = idx === 0 ? list.length - 1 : idx - 1;
                this.product = list[prev];
                return;
            }
        }
    },

    mounted() {
        // типо асинхронный запрос
        this.list = list;
    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";

$bluelink: #1652F0;

.heroProduct {
    display: flex;

    @include breakpoint(lg) {
        margin-bottom: 40px;
    }

    @include breakpoint(md) {
        flex-direction: column;
    }

    &Cart {
        margin-right: 30px;

        @include breakpoint(md) {
            margin-right: 0;
            margin-bottom: 40px;
        }

        &__block {
            margin-bottom: 16px;
            position: relative;
            background: #FFFFFF;
            border: 1px solid #ECEFF1;
            border-radius: 4px;
            width: 350px;
            height: 289px;
            text-align: center;

            p {
                @include text($size: 12px);
                color: #708598;
            }
        }

        &__image {
            width: 250px;
            height: 250px;
            margin: 15px auto 0;
            display: block;
        }

        // картинка на макете не правильная поэтому absolute поможет

        &__advertising {
            position: absolute;
            top: 15px;
            left: 15px;

            button {
                padding: 5px 13px;
                border-radius: 2px;
                display: block;
                border: none;
                @include text($size: 10px, $weight: 600);
                text-transform: uppercase;
                color: white;
                cursor: pointer;

                &:nth-child(1) {
                    background: #F2994A;
                    margin-bottom: 8px;
                }

                &:nth-child(2) {
                    background: #E92F2F;
                }
            }
        }

        &__list {
            position: absolute;
            top: 15px;
            right: 15px;
            padding: 2px 6px;
            background: white;
            border: solid 1px #1652F0;
            color: #1652F0;
            @include text($size: 12, $weight: 600);
            @include flexcenter;
            cursor: pointer;

            img {
                width: 15px;
                height: 15px;
                margin-right: 5px;
            }
        }

        &Slider {
            overflow: hidden;
            width: 350px;
            position: relative;

            &__wrapper {
                width: 280px;
                margin: 0 auto;
            }

            &__track {
                @include flexline;
            }

            &__item {
                cursor: pointer;

                &.active {
                    border: 2px solid #1652F0;
                    border-radius: 2px;
                }
            }

            img {
                width: 88px;
                height: 64px;
            }

            svg {
                position: absolute;
                top: 50%;
                transform: translateY(-50%);
                transform: rotate(90deg);
                cursor: pointer;

                path {
                    width: 6px;
                    height: 12px;
                }

                &:nth-child(1) {
                    right: 0;
                    transform: rotate(-90deg);
                }
            }
        }
    }

    &Content {
        &Box {
            display: flex;
            align-items: flex-start;
            margin-bottom: 15px;

            @include breakpoint(md) {
                text-align: center;
                flex-direction: column;
                align-items: center;
                margin-bottom: 40px;
            }

            &:nth-last-child(1) {
                margin-bottom: 0;
            }

            a {
                text-decoration: none;
                color: $bluelink;
                @include text;

                &:hover {
                    text-decoration: underline;
                }
            }

            img {
                margin-right: 10px;

                @include breakpoint(md) {
                    margin-right: 0;
                    margin-bottom: 20px
                }
            }

            &__info {
                p {
                    @include text;
                    margin-bottom: 8px;

                    span {
                        opacity: 0.6;
                    }
                }
            }

            &__views {
                p {
                    @include text;
                    color: #050F19;
                }
            }

            &__views>&__content {
                div {
                    @include flexcenter;

                    p {
                        @include text;

                        &:nth-child(1) {
                            margin-right: 14px;
                            border-bottom: dashed 2px #050F19;
                        }
                    }
                }
            }

            &__logo {
                padding-left: 28px;

                @include breakpoint(md) {
                    padding-left: 0;
                    @include flexcenter;
                }

                img {
                    width: 80px;
                    height: 80px;
                }
            }

            & &__title {
                @include text($weight: 600);
                margin-bottom: 8px;
                color: black;
            }

        }
    }
}
</style>