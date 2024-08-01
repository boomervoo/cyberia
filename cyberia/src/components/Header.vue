<template>
    <header class="header">
        <div class="container header-container">
            <a href="#" class="logo">
                <img class="logo__img" src="../img/logo.svg" alt="logo">
            </a>
            <nav class="nav">
                <ul class="nav__items list-reset">
                    <li class="nav__item">
                        <a class="nav__link" href="#">Агентство</a>
                    </li>
                    <li class="nav__item">
                        <a class="nav__link" href="#">Услуги</a>
                    </li>
                    <li class="nav__item">
                        <a class="nav__link" href="#">Кейсы</a>
                    </li>
                    <li class="nav__item">
                        <a class="nav__link" href="#">Блог</a>
                    </li>
                    <li class="nav__item">
                        <a class="nav__link" href="#">Контакты</a>
                    </li>
                </ul>
            </nav>
            <Burger v-if="burgerVisible" />
        </div>
    </header>
</template>

<script setup>
    
    import {ref, onMounted, onUnmounted } from 'vue';
    import Burger from './Burger.vue'; 

    const burgerVisible = ref(false);

    const checkWindowSize = () => {
        burgerVisible.value = window.innerWidth <= 768;
    };

    onMounted(() => {
        checkWindowSize();
        window.addEventListener('resize', checkWindowSize);
    });

    onUnmounted(() => {
        window.removeEventListener('resize', checkWindowSize);
    });
</script>

<style lang="scss">
    $padding: 73px;

    .header-container {
        display: flex;
        align-items: center;
        padding-top: $padding;
    }

    .logo {
        margin-right: 190px;
    }

    .nav {
        &__items {
            margin: 0;
            padding: 0;
            display: flex;
            gap: 63px;
        }

        &__item {
            color: #fff;
        }

        &__link {
            font-weight: 400;
            font-size: 15px;
            color: #fff;

            &:focus {
                outline-offset: 5px;
            }

            &:hover {
                color: #C4D2E3;
            }

            &:active {
                color: #C4D2E3;
            }
        }
    }

    @media (max-width: 1120px) {
        .logo {
            margin-right: 100px;
        }

        .nav__items {
            gap: 35px;
        }
    }

    @media (max-width: 768px) {
        .nav {
            display: none;
        }

        .logo {
            margin: 0;
        }

        .header-container {
            display: flex;
            justify-content: space-between;
        }
    }

    @media (max-width: 375px) {
        .header-container {
            padding-top: 55px;
            padding-bottom: 21px;
            background: #20212C;
        }
    }


</style>