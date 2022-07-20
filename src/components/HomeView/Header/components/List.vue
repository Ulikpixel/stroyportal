<template>
    <div class="headerList" @click="active = !active">
        <div :class="active ? 'headerList__icon active' : 'headerList__icon'">
            <img src="@/assets/images/icons/list.svg" alt="list/svg">
        </div>
        <p>Список</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            active: true
        }
    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";

.headerList {
    width: 111px;
    height: 40px;
    background: #FAFBFC;
    border: 1px solid #ECEFF1;
    border-radius: 4px;
    @include flexline;
    padding: 10px 16px;
    cursor: pointer;

    &__icon {
        height: 100%;
        position: relative;

        &.active {
            &::after {
                position: absolute;
                top: -2px;
                right: -2px;
                width: 5px;
                height: 5px;
                background: red;
                border-radius: 50%;
                border: solid 2px white;
                content: '';
            }
        }

        img {
            width: 16px;
            height: 20px;
        }
    }

    p {
        @include text($weight: 600);
    }
}
</style>