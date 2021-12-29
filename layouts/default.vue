<template>
<div>
    <nuxt />
</div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Ovo&display=swap');

* {
    font-family: 'Ovo', serif !important;
}
</style> 

<script>
export default {
    data() {
        return {

        }
    },

    mounted() {
        if (!localStorage.isDark || !localStorage.favorit || !localStorage.history) {
            localStorage.isDark = 'tidak';
            localStorage.favorit = JSON.stringify([]);
            localStorage.history = JSON.stringify([]);
        }
    }
}
</script>
