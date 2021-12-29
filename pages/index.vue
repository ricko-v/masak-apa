<template>
<div>
    <TopBar />
    <div class='container-fluid'>
        <div class='row'>
            <div class='col-sm-12 col-md-2 col-lg-4'></div>
            <div v-if='!item' class='col-sm-12 bg-white d-flex align-items-center justify-content-center min-100vh text-dark col-md-8 col-lg-4'>
                <div class="card bg-white" aria-hidden="true" style="width: 20rem;">
                    <div class="card-img-top placeholder-glow">
                        <span class="placeholder col-12 card-img-top" style='height:150px;'></span>
                    </div>
                    <div class="card-body">
                        <h5 class="card-title placeholder-glow">
                            <span class="placeholder col-12"></span>
                        </h5>
                        <p class="card-text placeholder-glow">
                            <span class="placeholder col-7"></span>
                        </p>
                        <p class="card-text placeholder-glow d-flex justify-content-center">
                            <span class="placeholder col-3"></span>
                            <span class="placeholder mx-4 col-3"></span>
                            <span class="placeholder col-3"></span>
                        </p>
                    </div>
                </div>
            </div>
            <div v-if='item' class='col-sm-12 mt-5 bg-white min-100vh text-dark pt-5 pb-5 col-md-8 col-lg-4'>
                <div v-for='data in item' class="card mx-auto mb-5 bg-white border-card shadow pb-3 " style="width: 20rem;">
                    <NuxtLink :to='"/detail-resep/" + data.key'>
                        <img :src="data.thumb" class="card-img-top" alt="">
                        <div class="card-body">
                            <h6 class="card-title text-primary">{{ data.title }}</h6>
                        </div>
                        <div class='d-flex'>
                            <div class='col justify-content-center d-flex align-items-center'>
                                <div class='mr-2'>
                                    <button data-bs-toggle="tooltip" data-bs-placement="bottom" title="perkiraan waktu membuat" class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                                        <svg xmlns="http://www.w3.org/2000/svg" class="icon-card text-secondary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                                        </svg>
                                    </button>
                                </div>
                                <small><small><small class='text-secondary'>{{ data.times }}</small></small></small>
                            </div>
                            <div class='col justify-content-center d-flex align-items-center'>
                                <div class='mr-2'>
                                    <button data-bs-toggle="tooltip" data-bs-placement="bottom" title="tingkat kesulitan" class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                                        <svg xmlns="http://www.w3.org/2000/svg" class="icon-card text-secondary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
                                        </svg>
                                    </button>
                                </div>
                                <small><small><small class='text-secondary'>{{ data.dificulty }}</small></small></small>
                            </div>
                            <div class='col justify-content-center d-flex align-items-center'>
                                <div class='mr-2'>
                                    <button data-bs-toggle="tooltip" data-bs-placement="bottom" title="perkiraan porsi" class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                                        <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" class="bi bi-people icon-card text-secondary" viewBox="0 0 16 16">
                                            <path d="M15 14s1 0 1-1-1-4-5-4-5 3-5 4 1 1 1 1h8zm-7.978-1A.261.261 0 0 1 7 12.996c.001-.264.167-1.03.76-1.72C8.312 10.629 9.282 10 11 10c1.717 0 2.687.63 3.24 1.276.593.69.758 1.457.76 1.72l-.008.002a.274.274 0 0 1-.014.002H7.022zM11 7a2 2 0 1 0 0-4 2 2 0 0 0 0 4zm3-2a3 3 0 1 1-6 0 3 3 0 0 1 6 0zM6.936 9.28a5.88 5.88 0 0 0-1.23-.247A7.35 7.35 0 0 0 5 9c-4 0-5 3-5 4 0 .667.333 1 1 1h4.216A2.238 2.238 0 0 1 5 13c0-1.01.377-2.042 1.09-2.904.243-.294.526-.569.846-.816zM4.92 10A5.493 5.493 0 0 0 4 13H1c0-.26.164-1.03.76-1.724.545-.636 1.492-1.256 3.16-1.275zM1.5 5.5a3 3 0 1 1 6 0 3 3 0 0 1-6 0zm3-2a2 2 0 1 0 0 4 2 2 0 0 0 0-4z" />
                                        </svg>
                                    </button>
                                </div>
                                <small><small><small class='text-secondary'>{{ data.portion }}</small></small></small>
                            </div>
                        </div>
                    </NuxtLink>

                </div>
                <infinite-loading @infinite="scrollData"></infinite-loading>
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
            item: null,
            page: 1
        }
    },

    methods: {
        scrollData($state) {

            if (this.item.length > 10) {
                for (let i = 0; i < 10; i++) {
                    this.item.shift();
                }
            }

            this.$axios('https://limitless-sea-61725.herokuapp.com/https://masak-apa-tomorisakura.vercel.app/api/recipes/' + this.page)
                .then(res => {
                    let h = res.data.results;

                    for (let i in h) {
                        this.item.push({
                            title: h[i].title,
                            key: h[i].key,
                            times: h[i].times,
                            portion: h[i].portion,
                            dificulty: h[i].dificulty,
                            thumb: h[i].thumb
                        })
                    }

                    this.page++;
                    $state.loaded();
                })
                .catch(err => {
                    alert(err)
                })
        }
    },

    mounted() {
        this.$axios('https://limitless-sea-61725.herokuapp.com/https://masak-apa-tomorisakura.vercel.app/api/recipes')
            .then(res => {
                this.item = [];
                let h = res.data.results;

                for (let i in h) {
                    this.item.push({
                        title: h[i].title,
                        key: h[i].key,
                        times: h[i].times,
                        portion: h[i].portion,
                        dificulty: h[i].dificulty,
                        thumb: h[i].thumb
                    })
                }
            })
            .catch(err => {
                alert('Ups... terjadi error! Silahkan refresh halaman')
            })
    }
}
</script>
