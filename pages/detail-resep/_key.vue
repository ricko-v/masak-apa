<template>
<div>
    <TopBar />
    <div class='container-fluid'>
        <div class='row'>
            <div class='col-sm-12 col-md-2 col-lg-4'></div>
            <div v-if='info.length == 0' class='col-sm-12 bg-white d-flex pt-5 mt-5 justify-content-center min-100vh text-dark col-md-8 col-lg-4'>
                <div class="bg-white w-100p" aria-hidden="true">
                    <div class="placeholder-glow rounded">
                        <span class="placeholder rounded col-12" style='height:200px;'></span>
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

            <div v-if='info.length !== 0' class='col-sm-12 min-100vh d-flex mt-5 pt-5 pb-5 bg-white col-md-8 col-lg-4'>
                <div v-for='data in info' class='w-100p rounded-top'>
                    <div>
                        <img :src='data.thumb' class='img-fluid rounded'>
                    </div>

                    <div class='mt-3'>
                        <h3 class='text-dark'>{{ data.title }}</h3>
                    </div>

                    <div>
                        <small class='text-secondary'>by {{ data.author.user }} | {{ data.author.datePublished }}</small>
                    </div>

                    <div class='mt-4 d-flex w-100p'>
                        <div class='col-4 d-flex justify-content-center align-items-center'>
                            <div class='text-center px-4 py-3 border border-secondary rounded'>
                                <button data-bs-toggle="tooltip" data-bs-placement="bottom" title="perkiraan waktu membuat" class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                                    <svg xmlns="http://www.w3.org/2000/svg" class="icon text-secondary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                                    </svg>
                                </button>
                                <p class='m-0 text-secondary' style='margin-top: -2px !important;'>
                                    <small>{{ data.times }}</small>
                                </p>
                            </div>
                        </div>
                        <div class='col-4 d-flex justify-content-center align-items-center'>
                            <div class='text-center px-4 py-3 border border-secondary rounded'>
                                <button data-bs-toggle="tooltip" data-bs-placement="bottom" title="tingkat kesulitan" class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                                    <svg xmlns="http://www.w3.org/2000/svg" class="icon-card text-secondary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
                                    </svg>
                                </button>
                                <p class='m-0 text-secondary' style='margin-top: -2px !important;'>
                                    <small>{{ data.dificulty }}</small>
                                </p>
                            </div>
                        </div>
                        <div class='col-4 d-flex justify-content-center align-items-center'>
                            <div class='text-center px-4 py-3 border border-secondary rounded'>
                                <button data-bs-toggle="tooltip" data-bs-placement="bottom" title="perkiraan" class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                                    <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" class="bi bi-people icon-card text-secondary" viewBox="0 0 16 16">
                                        <path d="M15 14s1 0 1-1-1-4-5-4-5 3-5 4 1 1 1 1h8zm-7.978-1A.261.261 0 0 1 7 12.996c.001-.264.167-1.03.76-1.72C8.312 10.629 9.282 10 11 10c1.717 0 2.687.63 3.24 1.276.593.69.758 1.457.76 1.72l-.008.002a.274.274 0 0 1-.014.002H7.022zM11 7a2 2 0 1 0 0-4 2 2 0 0 0 0 4zm3-2a3 3 0 1 1-6 0 3 3 0 0 1 6 0zM6.936 9.28a5.88 5.88 0 0 0-1.23-.247A7.35 7.35 0 0 0 5 9c-4 0-5 3-5 4 0 .667.333 1 1 1h4.216A2.238 2.238 0 0 1 5 13c0-1.01.377-2.042 1.09-2.904.243-.294.526-.569.846-.816zM4.92 10A5.493 5.493 0 0 0 4 13H1c0-.26.164-1.03.76-1.724.545-.636 1.492-1.256 3.16-1.275zM1.5 5.5a3 3 0 1 1 6 0 3 3 0 0 1-6 0zm3-2a2 2 0 1 0 0 4 2 2 0 0 0 0-4z" />
                                    </svg>
                                </button>
                                <p class='m-0 text-secondary' style='margin-top: -2px !important;'>
                                    <small>{{ data.portion }}</small>
                                </p>
                            </div>
                        </div>
                    </div>

                    <div class="accordion accordion-flush mt-5 mb-4" id="accordionFlushExample">
                        <div class="accordion-item rounded-top">
                            <h2 class="accordion-header" id="flush-headingOne">
                                <button class="accordion-button shadow-none rounded-top bg-white border border-secondary text-white collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapseOne" aria-expanded="false" aria-controls="flush-collapseOne">
                                    Deskripsi
                                </button>
                            </h2>
                            <div id="flush-collapseOne" class="accordion-collapse bg-white text-white border border-secondary collapse" aria-labelledby="flush-headingOne" data-bs-parent="#accordionFlushExample">
                                <div class="accordion-body">
                                    <small>{{ data.desc }}</small>
                                </div>
                            </div>
                        </div>
                        <div class="accordion-item">
                            <h2 class="accordion-header" id="flush-headingTwo">
                                <button class="accordion-button shadow-none bg-white border border-secondary text-white collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapseTwo" aria-expanded="false" aria-controls="flush-collapseTwo">
                                    Bahan
                                </button>
                            </h2>
                            <div id="flush-collapseTwo" class="accordion-collapse collapse bg-white text-white border border-secondary" aria-labelledby="flush-headingTwo" data-bs-parent="#accordionFlushExample">
                                <div class="accordion-body">
                                    <p v-for='bahan in data.ingredient'><small>{{ bahan }}</small></p>
                                </div>
                            </div>
                        </div>
                        <div class="accordion-item">
                            <h2 class="accordion-header" id="flush-headingThree">
                                <button class="accordion-button shadow-none bg-white border border-secondary text-white collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapseThree" aria-expanded="false" aria-controls="flush-collapseThree">
                                    Cara Membuat
                                </button>
                            </h2>
                            <div id="flush-collapseThree" class="accordion-collapse bg-white text-white border border-secondary collapse" aria-labelledby="flush-headingThree" data-bs-parent="#accordionFlushExample">
                                <div class="accordion-body">
                                    <p v-for='step in data.step'><small>{{ step.slice(2, step.length) }}</small></p>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div v-if='existFav' class="alert alert-danger" role="alert">
                        {{ existFav }}
                    </div>

                    <div v-if='succFav' class="alert alert-success" role="alert">
                        {{ succFav }}
                    </div>

                    <div class='mt-4'>
                        <button @click='tambahFav' class='shadow-none w-100p py-2 rounded bg-transparent text-white btn-outline-secondary'>Tambah ke favorit</button>
                    </div>

                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    transition: 'home',
    data() {
        return {
            info: [],
            existFav: '',
            succFav: ''
        }
    },

    methods: {
        tambahFav() {
            let arrFav = JSON.parse(localStorage.favorit);
            let cek = arrFav.find(x => x.key == this.$route.params.key);
            let data = {
                title: this.info[0].title,
                key: this.$route.params.key,
                thumb: this.info[0].thumb,
                portion: this.info[0].portion,
                times: this.info[0].times,
                dificulty: this.info[0].dificulty,
            }

            if (!cek) {
                arrFav.push(data);
                localStorage.favorit = JSON.stringify(arrFav);
                this.succFav = 'Resep ditambahkan ke favorit';
                setTimeout(() => {
                    this.succFav = '';
                }, 2000)
            } else {
                this.existFav = 'Resep sudah ada di favorit';
                setTimeout(() => {
                    this.existFav = '';
                }, 2000)
            }
        }
    },

    mounted() {

        this.$axios('https://limitless-sea-61725.herokuapp.com/https://masak-apa-tomorisakura.vercel.app/api/recipe/' + this.$route.params.key)
            .then(res => {
                let h = res.data.results;

                this.info.push({
                    thumb: h.thumb,
                    title: h.title,
                    portion: h.servings,
                    times: h.times,
                    dificulty: h.dificulty,
                    author: h.author,
                    step: h.step,
                    ingredient: h.ingredient,
                    desc: h.desc
                })
            })
            .catch(err => {
                alert('Ups... ada yang error. Mohon refresh halaman!' + err);
            });
    }
}
</script>
