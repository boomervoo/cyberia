<script setup>
    import Header from "./components/Header.vue" 
    import Breadcrumb from "./components/Breadcrumb.vue";
    import Projects from "./components/Projects.vue";
    import Feedback from "./components/Feedback.vue";
    import Footer from "./components/Footer.vue";

</script>

<template>
    <div class="app">
        <Header />
        <main class="main">
            <Breadcrumb />
            <Projects />
            <Feedback />
        </main>
        <Footer />
    </div>
</template>

<style lang="scss">
    @import url('./assets/global.scss');
</style>
