<script setup>

</script>

<template>
   <section class="crump">
        <div class="container">
            <div class="breadcrumb">
                <a class="breadcrumb-one" href="#">Главная</a> <span class="slash">&thinsp;/&thinsp;</span> <a class="breadcrumb-two" href="#">Кейсы</a>
            </div>
        </div>
   </section>
</template>

<style lang="scss">

    $fontSize: 12px;

    $padding: 65px;

    .crump {
        padding-top: $padding;
    }

    .breadcrumb {
        font-size: 14px;
    }
  
    .breadcrumb-one {
        font-weight: 400;
        font-size: 15px;
        color: #9aa8ba;

        &:focus {
            outline-offset: 5px;
        }
    }

    .slash {
        color: #9AA8BA;
    }

    .breadcrumb-two {
        font-weight: 400;
        font-size: 15px;
        color: #C4D2E3;
    }

    .breadcrumb-one:hover {
        color: #fff;
    }

    .breadcrumb-two:hover {
        color: #fff;
    }

    @media (max-width: 375px) {
        .breadcrumb-one {
            font-size: $fontSize;
        }

        .breadcrumb-two {
            font-weight: 300;
            color: #9aa8ba;
            font-size: $fontSize;
        }

        .crump {
            padding-top: 45px;
        }
    }
  
</style>