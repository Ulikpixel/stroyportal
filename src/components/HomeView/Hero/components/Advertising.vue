<template>
    <div class="heroAdvertising">
        <div class="heroAdvertising__line"></div>
        <div class="heroAdvertising__top">
            <img src="@/assets/images/icons/stars.svg" alt="stars/icon">
            <p>Популярное предложение</p>
        </div>
        <div class="heroAdvertising__price">
            <p>39 900 <span>РУБ/ ШТ</span></p>
            <p>В наличии</p>
        </div>
        <button class="heroAdvertising__btn">Перейти в магазин</button>
        <div class="heroAdvertising__bottom">
            <img src="@/assets/images/icons/correct.svg" alt="correct/icon">
            <div class="heroAdvertising__info">
                <p>Проверенный поставщик</p>
                <p>ООО ВсеИнструменты.ру</p>
                <div class="heroAdvertising__box">Дилер</div>
            </div>
            <img src="@/assets/images/icons/cart.svg" alt="cart/icon">
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";

$green: #05B169;

.heroAdvertising {
    background: #FFFFFF;
    width: 350px;
    height: 341px;
    border: 1px solid #ECEFF1;
    padding: 24px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.03);
    border-radius: 4px;
    overflow: hidden;
    position: relative;

    @include breakpoint(sm) {
        padding: 18px;
    }

    &__line {
        height: 4px;
        background: #FED83D;
        width: 100%;
        position: absolute;
        top: 0;
        left: 0;
    }

    &__top {
        margin-bottom: 28px;
        @include flexline($justify: flex-start);

        img {
            margin-right: 10px;
        }

        p {
            @include text($size: 10px, $weight: 600);
            text-transform: uppercase;
        }
    }

    &__price {
        margin-bottom: 30px;

        p {
            &:nth-child(1) {
                @include text($size: 28px, $weight: 700);

                span {
                    font-size: 14px;
                    font-weight: 600;
                }
            }

            &:nth-child(2) {
                @include text($size: 10px, $weight: 600);
                text-transform: uppercase;
                color: $green;
            }
        }
    }

    &__btn {
        padding: 11px 0;
        width: 100%;
        margin-bottom: 32px;
        background: $orange;
        border-radius: 4px;
        cursor: pointer;
        border: solid 2px $orange;
        @include text($weight: 600);
        transition: .8s;

        &:hover {
            background: white;
        }
    }

    &__bottom {
        @include flexline($align: flex-start);

        img {
            &:nth-child(1) {
                width: 48px;
                height: 48px;
            }

            &:nth-child(2) {
                width: 42px;
                height: 20px;
            }
        }
    }

    &__info {
        p {
            margin-bottom: 6px;

            &:nth-child(1) {
                color: $green;
                @include text($weight: 600, $size: 10px);
                text-transform: uppercase;
                margin-bottom: 2px;
            }

            &:nth-child(2) {
                @include text($weight: 600);
            }
        }
    }

    &__box {
        text-transform: uppercase;
        width: 60px;
        height: 20px;
        background: #E5FFF0;
        border-radius: 2px;
        color: $green;
        @include text($weight: 600, $size: 10px);
        @include flexcenter;
    }
}
</style>