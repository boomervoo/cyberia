<template>
    <section class="projects">
        <div class="container">
            <h2 class="title">Кейсы</h2>
            <ul class="list-reset projects__items">
                <li class="projects__item" v-for="item in items" :key="item.id"> 
                    <a class="projects__link" href="#" @click.prevent="() => selectCategory(item.id)">
                        <button class="projects__btn btn-reset">
                            {{ item.name }}
                        </button>
                    </a>
                </li>
            </ul>

            <ul class="list-reset cards__items">
                <li class="cards__item" v-for="card in filteredCards" :key="card.id">
                    <article class="card">
                        <a class="card__link" href="#">
                            <img :src="card.image" alt="image" class="card__image card__arrow">
                            <div class="card__title">
                                <!-- <div class="arrow">
                                    <svg class="card__arrow" width="25" height="25" viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
                                        <rect width="24.9999" height="5.46874" rx="1" transform="matrix(1 0 0 -1 0 24.9995)" fill="#2D76F9"/>
                                        <rect width="14.0625" height="5.46874" rx="1" transform="matrix(1 0 0 -1 10.938 14.0625)" fill="#2D76F9"/>
                                        <rect width="24.9999" height="5.46874" rx="1" transform="matrix(0 1 1 0 0 0.00012207)" fill="#2D76F9"/>
                                        <rect width="14.0625" height="5.46874" rx="1" transform="matrix(0 1 1 0 10.938 0.00012207)" fill="#2D76F9"/>
                                    </svg>
                                </div> -->
                                <span class="offer__title">
                                    {{ card.title }}
                                </span>
                            </div>
                            <div class="card__overlay">
                                <!-- <div class="arrow--overlay">
                                    <svg width="17" height="17" viewBox="0 0 17 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                                        <rect width="17" height="3.71798" rx="0.886243" transform="matrix(1 0 0 -1 0 17)" fill="white" />
                                        <rect width="9.56253" height="3.71798" rx="0.886243" transform="matrix(1 0 0 -1 7.43359 9.56641)" fill="white" />
                                        <rect width="16.9965" height="3.71872" rx="0.886243" transform="matrix(0 1 1 0 0 0)" fill="white" />
                                        <rect width="9.56053" height="3.71875" rx="0.886243" transform="matrix(0 1 1 0 7.43359 0)" fill="white" />
                                    </svg>
                                </div> -->
                                <h3 class="card__title--overlay">{{ card.title }}</h3>
                                <p class="card__description">
                                    Онлайн гипермаркет. Для компании были разработаны сайт и мобильное приложение и т.д.
                                </p>
                            </div>
                        </a>
                    </article>
                </li>
            </ul>
        </div>
    </section>
</template>

<script setup>
    import { ref, onMounted, computed } from 'vue'; // подключаем реактивную функцию и хук жизн.цикла
    import axios from 'axios'; // подключаем библиотеку для работы с API

    const items = ref([]); 
    const cardElements = ref([]);
    const selectedCategory = ref(null);

    const selectCategory = (categoryId) => {
        selectedCategory.value = categoryId;
        console.log('Selected Category:', selectedCategory.value);
    }

    const filteredCards = computed(() => {
        if (!selectedCategory.value) {
            return cardElements.value;
        }
        return cardElements.value.filter(card => 
            card.categories.some(category => category.id === selectedCategory.value)
        );
    })

    onMounted(() => {
    axios.get('https://api.test.cyberia.studio/api/v1/project-categories')
        .then(response => {
            items.value = response.data.items;
            console.log('Items:', items.value);
        })
        .catch(error => {
            console.error('Ошибка при выполнении GET запроса:', error);
        });

        axios.get('https://api.test.cyberia.studio/api/v1/projects')
        .then(response => {
            console.log('API Response:', response.data); // Логируем данные API
            cardElements.value = response.data.items;
            console.log('Card Elements:', cardElements.value); // Логируем сохраненные данные
        })
        .catch(error => {
            console.error('Ошибка при выполнении GET запроса:', error);
        });
    });
</script>

<style lang="scss">
    $colorTitle: #313341;

    .title {
        margin: 0;
        margin-bottom: 72px;
        font-weight: 600;
        font-size: 43px;
        color: #eef3ff;
    }

    .projects {
        padding-top: 130px;
        padding-bottom: 103px;

        &__items {
            margin: 0;
            margin-bottom: 53px;
            padding: 0;
            display: flex;
            justify-content: space-between;
        }

        &__item {
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 7px;
            box-shadow: 8px 15px 29px 0 rgba(33, 33, 34, 0.41);
            background-color: #313341;
            transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out, background 0.3s ease-in-out;  
            cursor: pointer;

            &__link:focus {
                background: #3475ee;
            }

            &:hover {
                transform: scale(1.05);
                box-shadow: 0 8px 12px rgba(0, 0, 0, 0.2);
            }

            &:active {
                background: #2d76f9;
            }
        }

        &__link {
            padding: 10px 29px;
        }
        
        &__link:focus {
            border-top-left-radius: 7px;
            border-bottom-left-radius: 7px;
            border-top-right-radius: 7px;
            border-bottom-right-radius: 7px;
            outline: 10px;
            background: #3475ee;
        }

        &__btn {
            font-weight: 400;
            font-size: 22px;
            color: #eef3ff;
            letter-spacing: 1px;
            transition: color 0.3s ease-in-out;
            
            &:focus {
                outline: none;
                outline-offset: none
            }
        }

    }

    .cards__items {
        margin: 0;
        padding: 0;
        display: flex;
        flex-wrap: wrap;
        gap: 40px;
        row-gap: 31px;
   }

   .cards__item {
        position: relative;
        width: calc((100% - (40px * 2)) / 3);
        height: 378px;
    }

    .card {
        position: relative;
        transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;

        &__image {
            height: 378px;
            border-radius: 12px;
        }

        &__link {
            display: block;
            font-weight: 600;
            font-size: 20px;
            color: #fff;
        }

        &__title {
            position: absolute;
            display: flex;
            align-items: center;
            text-align: center;
            justify-content: center;
            top: 23px;
            right: 27px;
            width: 122px;
            height: 122px;
            border-radius: 5px;
            background: $colorTitle;

            &::before {
                position: absolute;
                content: '';
                background-image: url('../img/arrow.svg');
                width: 25px;
                height: 25px;
                top: -5px;
                right: -7px;
            }
        }

        &__overlay {
            display: none;
            position: absolute;
            flex-direction: column;
            justify-content: flex-end;
            bottom: 0;
            left: 0;
            right: 0;
            padding: 29px 29px 24px 28px;
            border-radius: 12px;
            background: linear-gradient(0deg, #090b21 0%, rgba(49, 51, 65, 0) 100%);
            color: white;
            height: 100%;

            &::before {
                position: absolute;
                content: '';
                background-image: url('../img/arrow-mobile.svg');
                width: 17px;
                height: 17px;
                top: 60%;
            }
        }

        &__description {
            margin: 0;
            font-weight: 400;
            font-size: 13px;
            color: #fff;
            letter-spacing: 0.3px;
            line-height: 18px;
        }
    }

    .card:hover {
        transform: scale(1.05);
        box-shadow: 0 8px 12px rgba(0, 0, 0, 0.2);
    }

    .offer__title {
        max-width: 77px;
        text-align: start;
        line-height: 28px;
    }

    .arrow {
        position: absolute;
        top: -7px;
        right: -7px;
    }

    @media (max-width:1120px) {
        .cards__item {
            width: calc((100% - (40px * 1)) / 2);
        }

        .projects {
            &__items {
                justify-content: center;
                align-items: center;
                display: flex;
                flex-wrap: wrap;
                gap: 30px;
            }

            &__item {
                width: calc((100% - (40px * 1)) / 2);
            }
        }
    }

    @media (max-width: 768px) {

        .cards__item {
            width: calc(100% / 1);
        }

        .projects {
            padding-top: 70px;
        }

        .projects__btn {
            font-size: 20px;
        }
    }

    @media (max-width: 576px) {
        .projects__btn {
            font-size: 14px;
        }
    }

    @media (max-width: 375px) {

        .logo__img {
            max-width: 93px;
        }

        .projects {
            padding-top: 32px;
            padding-bottom: 48px;
        }

        .projects__items {
            margin-bottom: 41px;
            gap: 8px;
            row-gap: 18px;
        }

        .projects__item {
            width: calc((100% - 8px) / 2);
        }

        .projects__link {
            padding: 7px 0px;
        }

        .card {
            max-height: 320px;
        }

        .card__image {
            height: 320px;
            transform: scale(-1, 1);
        }

        .cards__items {
            row-gap: 20px;
        }

        .cards__item {
            height: 100%;
        }

        .title {
            margin-bottom: 46px;
            font-weight: 500;
            font-size: 21px;
            letter-spacing: 0.7px;
        }

        .projects__btn {
            font-size: 11px;
        }

        .card__overlay {
            display: flex;
        }

        .card__title {
            display: none;
        }

        .card__title--overlay {
            margin: 0;
            margin-bottom: 5px;
            font-weight: 500;
            font-size: 18px;
            letter-spacing: 0.65px;
            color: #fff;
        }

    }
</style>