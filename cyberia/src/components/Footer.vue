<template>
    <footer class="footer">
        <div class="container footer__container">
            <div class="footer__logo">
                <a href="#" class="logo">
                    <img class="img-logo" src="../img/logo.svg" alt="logo">
                </a>
                <span class="footer__sub--title">
                    Веб-разработка&nbsp;и усиление IT-команд
                </span>
            </div>
            <div class="footer__wrapper">
                <address class="address">
                    <ul class="address__items list-reset">
                        <li class="address__item">
                            <a href="tel:+79991234567" class="address__link address__phone">+7 999 123 45 67</a>
                        </li>
                        <li class="address__item">
                            <a href="mailto: hello@cyberia.studio" class="address__link address__email">hello@cyberia.studio</a>
                        </li>
                        <li class="address__item">
                            <p class="address__descr">ул.Ярных, д.35, оф.10</p>
                        </li>
                    </ul>
                </address>
                <nav class="nav footer__nav">
                    <ul class="nav__items--footer list-reset">
                        <li class="nav__item">
                            <a class="nav__link" href="#">Агентство</a>
                        </li>
                        <li class="nav__item">
                            <a class="nav__link" href="#">Услуги</a>
                        </li>
                        <li class="nav__item">
                            <a class="nav__link" href="#">Кейсы</a>
                        </li>
                    </ul>
                    <ul class="nav__items--footer list-reset">
                        <li class="nav__item">
                            <a class="nav__link" href="#">Блог</a>
                        </li>
                        <li class="nav__item">
                            <a id="nav-contact" class="nav__link" href="#">Контакты</a>
                        </li>
                    </ul>
                </nav>
            </div>
        </div>
    </footer>
</template>

<script setup>

    function updateContactText () {
        const contactLink = document.getElementById('nav-contact')

        if(window.innerWidth <= 375) {
            contactLink.textContent = 'Вопросы'
        } else {
            contactLink.textContent = 'Контакты'
        }
    }

    window.addEventListener('resize', updateContactText);
    window.addEventListener('load', updateContactText);
</script>

<style lang="scss">
    @mixin resetMarginPadding {
        margin: 0;
        padding: 0;
    }

    :root {
        --fontSize: 13px;
    }

    @mixin textStyle {
        font-style: normal;
        font-weight: 400;
        font-size: 16px;
        letter-spacing: -0.1px;
        color: #fff;
    }

    .footer {
        padding-top: 130px;
        padding-bottom: 150px;
        background: #313341;

        &__container {
            display: flex;
            gap: 155px;
        }

        &__wrapper {
            display: flex;
        }

        &__logo {
            max-width: 197px;
        }

        &__nav {
            display: flex;
            gap: 70px;
        }
    }

    .address {

        margin-right: 53px;

        &__items {
            @include resetMarginPadding;
        }

        &__item:not(:last-child) {
            margin-bottom: 27px;
        }

        &__descr {
            @include resetMarginPadding;
            @include textStyle;
        }

        &__link {
            @include textStyle;

            &:hover {
                color: #C4D2E3;
            }

            &:active {
                color: #C4D2E3;
            }
        }

        &__phone {
            font-size: 15px;
        }

        &__email {
            font-size: 17px;
        }
    }

    .footer__sub--title {
        font-weight: 400;
        font-size: 16px;
        line-height: 21px;
        color: #fff;
    }


    .nav__items--footer {
        display: flex;
        flex-direction: column;
        gap: 28px;
        margin: 0;
        padding: 0;
    }

    .img-logo {
        padding-bottom: 25px;
    }

    @media (max-width: 1120px) {
        .footer__nav {
            gap: 50px;
        }

        .address {
            margin-right: 45px;
        }

        .footer__container {
            gap: 100px;
        }
    }

    @media (max-width: 768px) {
        .footer__container {
            flex-direction: column;
            align-items: center;
            gap: 70px;
        }

        .footer__logo {
            display: flex;
            max-width: 234px;
            align-items: center;
            flex-direction: column;
        }

        .address {
            margin-right: 70px;
        }

        .footer__nav {
            gap: 70px;
        }

        .footer__sub--title {
            display: inline-flex;
        }

        .footer {
            padding-top: 95px;
            padding-bottom: 95px;
        }
    }

    @media (max-width: 576px) {

        .address {
            margin-right: 30px;
        }

        .footer__nav {
            gap: 40px;
        }

        .address__link,
        .address__descr,
        .nav__link {
            font-size: var(--fontSize);
        }

        .footer__sub--title  {
            font-size: var(--fontSize);
        }
    
    }

    @media (max-width: 375px) {
        .footer {
            padding-top: 29px;
            padding-bottom: 47px;
        }

        .footer__container {
            gap: 36px;
        }
        
        .img-logo {
            padding-bottom: 7px;
            max-width: 102px;
        }

        .footer__sub--title {
            max-width: 207px;
            text-align: center;
            line-height: 19px;
        }

        .address__item:not(:last-child) {
            margin-bottom: 24px;
        }

        .address {
            margin-right: 14px;
        }

        .nav__items--footer {
            gap: 23px;
        }

        .footer__nav {
            gap: 46px;
        }
    }

    @media (max-width: 320px) {
        .checkbox__btn {
            padding: 14px 101px;
        }
    }
</style>