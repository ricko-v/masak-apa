<template>
<div>
    <TopBar />
    <div class='container-fluid'>
        <div class='row'>
            <div class='col-sm-12 col-md-2 col-lg-4'></div>
            <div class='col-sm-12 bg-white min-100vh d-flex justify-content-center align-items-center text-white col-md-8 col-lg-4'>
                <div class='w-100p'>
                    <div class='text-center mt-2'>
                        <h5>Cari Resep</h5>
                        <div class="input-group mt-3">
                            <input type="text" @keyup.enter='cari' v-model='key' class="form-control shadow-none text-white bg-white" placeholder="Masukan kata kunci" aria-label="query" aria-describedby="basic-addon1">
                            <span class="input-group-text bg-white" id="basic-addon1">
                                <button @click='cari' class='bg-transparent d-flex align-items-center shadow-none border-0'>
                                    <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" class="bi bi-search icon-card text-white" viewBox="0 0 16 16">
                                        <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z" />
                                    </svg>
                                </button>
                            </span>
                        </div>
                        <div class='text-start mt-2'>
                            <NuxtLink to='/histori' class='text-primary'><small>Histori Pencarian</small></NuxtLink>
                        </div>
                    </div>
                </div>
            </div>
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
            list: [],
            key: ''
        }
    },

    methods: {
        cari() {
            this.$router.push({
                path: '/cari-resep/' + this.key
            });

            let arrHistory = JSON.parse(localStorage.history);

            arrHistory.push(this.key);

            let arr = Array.from(new Set(arrHistory));

            localStorage.history = JSON.stringify(arr);
        }
    }

}
</script>
