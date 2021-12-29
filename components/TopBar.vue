<template>
<div>
    <div class='container-fluid position-fixed fixed-top'>
        <div class='row'>
            <div class='col-sm-12 col-md-2 col-lg-4'></div>
            <div class='col-sm-12 py-3 bg-white border-bottom border-secondary bot-bottom-radius col-md-8 col-lg-4'>
                <div class='d-flex text-dark align-items-center justify-content-between'>
                    <div>
                        <b v-if='path !== "kategori-resep" && path !== "detail-resep" && path !== "histori" && path !== "cari-resep" && path !== "tentang"'>
                            <NuxtLink class='text-white' to='/tentang'>Masak Apa</NuxtLink>
                        </b>
                        <button v-if='path == "kategori-resep"' @click='redirect("/kategori")' class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon text-dark" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 17l-5-5m0 0l5-5m-5 5h12" />
                            </svg>
                        </button>
                        <button v-if='path == "detail-resep"' @click='redirect("/")' class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon text-dark" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 17l-5-5m0 0l5-5m-5 5h12" />
                            </svg>
                        </button>
                        <button v-if='path == "histori"' @click='redirect("/cari")' class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon text-dark" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 17l-5-5m0 0l5-5m-5 5h12" />
                            </svg>
                        </button>
                        <button v-if='path == "cari-resep"' @click='redirect("/cari")' class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon text-dark" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 17l-5-5m0 0l5-5m-5 5h12" />
                            </svg>
                        </button>
                        <button v-if='path == "tentang"' @click='redirect("/")' class='shadow-none border-0 bg-transparent mx-auto mb-1'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon text-dark" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 17l-5-5m0 0l5-5m-5 5h12" />
                            </svg>
                        </button>
                    </div>
                    <div>
                        <button v-if='isDark == "tidak" || isDark == ""' @click='ubahTema' class='shadow-none border-0 bg-transparent'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" />
                            </svg>
                        </button>
                        <button v-if='isDark == "benar"' @click='ubahTema' class='shadow-none text-white border-0 bg-transparent'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z" />
                            </svg>
                        </button>
                    </div>
                </div>
            </div>
            <div class='col-sm-12 col-md-2 col-lg-4'></div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            isDark: '',
            path: ''
        }
    },

    methods: {
        redirect(path) {
            this.$router.push({
                path: path
            })
        },

        ubahTema() {
            if (localStorage.isDark == 'tidak') {
                this.isDark = 'benar';
                let div = document.querySelectorAll('.bg-white');
                let teks = document.querySelectorAll('.text-dark');
                let primary = document.querySelectorAll('.text-primary');
                for (let i = 0; i < div.length; i++) {
                    div[i].classList.remove("bg-white");
                    div[i].classList.add("bg-dark");
                }
                for (let a = 0; a < teks.length; a++) {
                    teks[a].classList.remove("text-dark");
                    teks[a].classList.add("text-white");
                }
                for (let a = 0; a < primary.length; a++) {
                    primary[a].classList.remove("text-primary");
                    primary[a].classList.add("text-warning");
                }

                localStorage.isDark = 'benar';
            } else {
                this.isDark = false;
                let div = document.querySelectorAll('.bg-dark');
                let teks = document.querySelectorAll('.text-white');
                let primary = document.querySelectorAll('.text-warning');
                for (let i = 0; i < div.length; i++) {
                    div[i].classList.remove("bg-dark");
                    div[i].classList.add("bg-white");
                }
                for (let a = 0; a < teks.length; a++) {
                    teks[a].classList.remove("text-white");
                    teks[a].classList.add("text-dark");
                }
                for (let a = 0; a < primary.length; a++) {
                    primary[a].classList.remove("text-warning");
                    primary[a].classList.add("text-primary");
                }
                localStorage.isDark = 'tidak';
                this.isDark = 'tidak';
            }
        },

        cekTema() {
            if (localStorage.isDark == 'benar') {
                let div = document.querySelectorAll('.bg-white');
                let teks = document.querySelectorAll('.text-dark');
                let primary = document.querySelectorAll('.text-primary');
                for (let i = 0; i < div.length; i++) {
                    div[i].classList.remove("bg-white");
                    div[i].classList.add("bg-dark");
                }
                for (let a = 0; a < teks.length; a++) {
                    teks[a].classList.remove("text-dark");
                    teks[a].classList.add("text-white");
                }
                for (let a = 0; a < primary.length; a++) {
                    primary[a].classList.remove("text-primary");
                    primary[a].classList.add("text-warning");
                }
            } else {
                let div = document.querySelectorAll('.bg-dark');
                let teks = document.querySelectorAll('.text-white');
                for (let i = 0; i < div.length; i++) {
                    div[i].classList.remove("bg-dark");
                    div[i].classList.add("bg-white");
                }
                for (let a = 0; a < teks.length; a++) {
                    teks[a].classList.remove("text-white");
                    teks[a].classList.add("text-dark");
                }
            }
        }
    },

    mounted() {
        if (!localStorage.isDark) {
            this.isDark = 'tidak';
        } else {
            this.isDark = localStorage.isDark;
        }

        let cekTema = this.cekTema;

        function cek() {
            setTimeout(() => {
                cekTema();
                cek()
            }, 100);
        }
        cek();

        let path = this.$route.path.split('/')[1];
        this.path = path;
    }
}
</script>
