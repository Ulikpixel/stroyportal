<template>
    <header class="header">
        <div class="headerTop">
            <div class="container">
                <div class="headerTop__point">
                    <img src="@/assets/images/icons/point.svg" alt="point/icon">
                    <p>Волгоградская область</p>
                </div>
                <nav class="headerTop__nav">
                    <button>Тендеры</button>
                    <button>База подрядчиков</button>
                    <button>
                        Другие сервисы
                        <img src="@/assets/images/icons/arrow.svg" alt="arrow/icon">
                    </button>
                </nav>
            </div>
        </div>
        <div class="headerBottom">
            <img src="@/assets/images/logo.png" alt="logo" class="headerBottom__logo--mobile">
            <Popup :active="menu" @click="toggleMenu" />
            <button class="hamburger hamburger--collapse" :class="menu ? 'is-active' : ''" type="button" @click="toggleMenu">
                <span class="hamburger-box">
                    <span class="hamburger-inner"></span>
                </span>
            </button>
            <nav :class="menu ? 'container active' : 'container'">
                <div class="headerBottom__left">
                    <img src="@/assets/images/logo.png" alt="logo" class="headerBottom__logo">
                    <Catalog />
                    <Search />
                </div>
                <div class="headerBottom__right">
                    <List />
                    <Avatar fullname="Keneshbekov Ulugbek" />
                </div>
            </nav>
        </div>
    </header>
</template>

<script>
import Catalog from "@/components/HomeView/Header/components/Catalog";
import Search from "@/components/HomeView/Header/components/Search";
import List from "@/components/HomeView/Header/components/List";

export default {
    data() {
        return {
            menu: false,
        }
    },
    components: {
        Catalog,
        Search,
        List
    },
    methods: {
        toggleMenu() {
            this.menu = !this.menu
        }
    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";

.header {
    min-height: 32px;

    &Top {
        background: $bg;
        min-height: 32px;
        @include flexcenter;
        padding: 8px 0;

        .container {
            @include flexline;

            @include breakpoint(sm) {
                flex-direction: column;
            }
        }

        p,
        button {
            font-weight: 400;
            font-size: 12px;
            font-family: $opensans;
            color: #708598;
        }

        &__point {
            @include flexline;

            @include breakpoint(sm) {
                margin-bottom: 5px;
            }

            img {
                width: 12px;
                height: 14px;
                margin-right: 8px;
            }
        }

        &__nav {
            @include flexline(wrap);
            justify-content: center;

            button {
                border: none;
                background: none;
                margin-right: 24px;

                &:nth-last-child(1) {
                    margin-right: 0;

                    img {
                        width: 10px;
                        height: 6px;
                        margin-left: 5px;
                    }
                }
            }
        }
    }

    &Bottom {
        min-height: 76px;
        border: solid 1px #FFFFFF;
        @include flexcenter;

        @include breakpoint(lg) {
            justify-content: space-between;
            padding: 0 15px;
        }

        .container {
            @include flexline(wrap);

            @include breakpoint(lg) {
                background: white;
                position: fixed;
                top: 0;
                right: -400px;
                width: 350px;
                height: 100%;
                z-index: 90;
                transition: 0.8s;
                flex-direction: column;
                justify-content: flex-start;

                &.active {
                    right: 0;
                }
            }
        }

        .hamburger {
            display: none;
            z-index: 99;
            position: absolute;
            right: 0;

            @include breakpoint(lg) {
                display: block;
            }
        }

        &__logo {
            width: 221px;
            height: 48px;

            @include breakpoint(lg) {
                display: none;
            }

            &--mobile {
                display: none;

                @include breakpoint(lg) {
                    display: block;
                }
            }
        }

        &__right,
        &__left {
            @include flexline(wrap);
        }

        &__left {
            @include breakpoint(lg) {
                padding-top: 100px;
                flex-direction: column-reverse;
                width: 100%;
            }

             @include breakpoint(sm) {
                padding-top: 120px;
             }

            .search {
                @include breakpoint(lg) {
                    width: 100%;
                    margin-bottom: 10px;
                }
            }
        }

        &__right {
            .avatar {
                @include breakpoint(lg) {
                    position: absolute;
                    top: 50px;
                    left: 15px;
                }
                 @include breakpoint(sm) {
                    top: 73px;
                 }
            }

            .list {
                @include breakpoint(lg) {
                    margin-top: 10px;
                }
            }
        }

        &__logo,
        .headerList,
        .headerCatalog {
            margin-right: 24px;

            @include breakpoint(lg) {
                margin-right: 0;
                margin-bottom: 10p;
            }
        }
    }
}
</style>