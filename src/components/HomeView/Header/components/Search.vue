<template>
    <div :class="list.length && value.length ? 'headerSearch active' : 'headerSearch'" id="search">
        <input type="text" placeholder="Cтроительные смеси" :value="value" @input="search">
        <div class="headerSearch__icon" @click="getName">
            <img src="@/assets/images/icons/search.svg" alt="search/icon">
        </div>
        <ul class="headerSearch__list" v-if="list.length && value.length">
            <li v-for="(name, index) in list" :key="`${index}${name}`" @click="chooseName(name)">{{ name }}</li>
        </ul>
    </div>
</template>

<script>
const names = ["Бесто", "Боларс", "Старатели", "Русеан", "Кнауф", "Каменный цветок", "Юнис", "Атлас", "Ивсил", "Мансуровские смеси"]

export default {
    data() {
        return {
            value: "",
            list: []
        }
    },
    methods: {
        search(e) {
            const value = e.target.value;
            const list = names.filter(str => str.toLowerCase().includes(value.trim().toLowerCase()))

            this.value = value;
            this.list = list;

            // обычно поисковик работает через асинхронный запрос
            // Пример:
            // const res = await axios.get(`${url}*?name=${value}`)
            // this.list = res;
        },
        chooseName(name) {
            this.value = name;
            this.list = [];
        },
        getName() {
            // в тз не указано какая должна быть логика поэтому пусть данные отправлят в консоль
            if (this.value.length >= 2) {
                console.log(this.value);
                this.value = "";
                this.list = [];
            }
        }
    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";

.headerSearch {
    width: 248px;
    height: 40px;
    border-radius: 4px;
    border: 1px solid #ECEFF1;
    position: relative;

    @include breakpoint(lg) {
        margin-bottom: 20px;
    }

    &.active {
        border-bottom: none;
    }

    input {
        width: 100%;
        height: 100%;
        border: none;
        padding-left: 15px;
        padding-right: 28px;
        border-radius: 5px;
        @include text;
    }

    &__icon {
        position: absolute;
        top: 0;
        right: 9px;
        height: 100%;
        @include flexcenter;
        cursor: pointer;

        &.active {
            border: solid 1px red;
        }

        img {
            width: 20px;
            height: 20px;
        }
    }

    &__list {
        background: white;
        position: absolute;
        top: 100%;
        left: 0;
        width: 100%;
        border: 1px solid #ECEFF1;
        border-top: none;
        max-height: 300px;
        overflow-y: scroll;

        li {
            padding: 5px 10px;
            cursor: pointer;
            @include text;

            &:hover {
                background: rgb(233, 233, 233);
            }

            &:nth-last-child(1) {
                margin-bottom: 0;
            }
        }

        &::-webkit-scrollbar {
            width: 10px;
            height: 8px;
            background: rgb(219, 219, 219);

            &-thumb {
                background-color: $orange;
                box-shadow: inset 1px 1px 10px #f3faf7;
            }
        }

    }
}
</style>