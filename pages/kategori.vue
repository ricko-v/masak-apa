<template>
<div>
    <TopBar />
    <div class='container-fluid'>
        <div class='row'>
            <div class='col-sm-12 col-md-2 col-lg-4'></div>
            <div class='col-sm-12 min-100vh d-flex mt-5 pt-5 mb-5 pb-5 bg-white col-md-8 col-lg-4'>
                <div class='w-100p'>
                    <div class='kategori text-dark px-2 py-2 mx-3'>
                        <p class='border-bottom border-secondary pb-2 px-1'>Kategori Resep</p>
                        <div v-if='list.length == 0'>
                            <p class="card-text placeholder-glow">
                                <span class="placeholder col-12"></span>
                                <span class="placeholder col-12"></span>
                            </p>
                        </div>
                        <p v-for='k in list' class='py-2 m-0'>
                            <button @click='redirect("/kategori-resep/" + k.key)' class='w-100p text-start bg-transparent shadow-none border-0 text-primary'><small>{{ k.text }}</small></button>
                        </p>
                    </div>
                </div>
            </div>
            <div class='col-sm-12 col-md-2 col-lg-4'></div>
        </div>
    </div>
    <BotBar />
</div>
</template>

<script>
export default {
    transition: 'home',
    data() {
        return {
            list: []
        }
    },

    methods: {
        redirect(path) {
            this.$router.push({
                path: path
            })
        }
    },

    mounted() {
        this.$axios('https://limitless-sea-61725.herokuapp.com/https://masak-apa-tomorisakura.vercel.app/api/categorys/recipes')
            .then(res => {
                let response = res.data.results;

                for (let i in response) {
                    this.list.push({
                        text: response[i].category,
                        key: response[i].key
                    });
                }
            })
            .catch(err => {
                alert('Ups... ada yang error. Mohon refresh halaman!');
            });
    }
}
</script>
