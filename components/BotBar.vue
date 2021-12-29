<template>
<div>
    <div class='container-fluid position-fixed fixed-bottom'>
        <div class='row'>
            <div class='col-sm-12 col-md-2 col-lg-4'></div>
            <div class='col-sm-12 py-2 bg-white border-top border-secondary bot-top-radius shadow col-md-8 col-lg-4'>
                <div class='d-flex justify-content-around'>
                    <div class='text-center'>
                        <button @click='redirect("/")' :class="[path == '/' ? 'text-primary' : 'text-secondary']" class='shadow-none border-0 bg-transparent'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" />
                            </svg>
                            <div>
                                <small>Beranda</small>
                            </div>
                        </button>
                    </div>
                    <div class='text-center'>
                        <button @click='redirect("/kategori")' :class="[path == '/kategori' ? 'text-primary' : 'text-secondary']" class='shadow-none border-0 bg-transparent'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10" />
                            </svg>
                            <div>
                                <small>Kategori</small>
                            </div>
                        </button>
                    </div>
                    <div class='text-center'>
                        <button @click='redirect("/favorit")' :class="[path == '/favorit' ? 'text-primary' : 'text-secondary']" class='shadow-none border-0 bg-transparent'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
                            </svg>
                            <div>
                                <small>Favorit</small>
                            </div>
                        </button>
                    </div>
                    <div class='text-center'>
                        <button @click='redirect("/cari")' :class="[path == '/cari' ? 'text-primary' : 'text-secondary']" class='shadow-none border-0 bg-transparent'>
                            <svg xmlns="http://www.w3.org/2000/svg" class="icon" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
                            </svg>
                            <div>
                                <small>Cari</small>
                            </div>
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
            path: ''
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
        let path = this.$route.path;
        this.path = path;
    }
}
</script>