<template>
<div>
    <TopBar />
    <div class='container-fluid'>
        <div class='row'>
            <div class='col-sm-12 col-md-2 col-lg-4'></div>
            <div class='col-sm-12 bg-white min-100vh d-flex justify-content-center pt-10p text-white col-md-8 col-lg-4'>
                <div class='w-100p mt-3'>
                    <div class='text-center'>
                        <h5>Histori Pencarian</h5>
                    </div>
                    <div v-if='item.length == 0' class="alert border-secondary border mt-4" role="alert">
                        <small>Kamu belum pernah mencari resep apapun.</small>
                    </div>
                    <div class='mt-4'>
                        <div v-for='teks in item' :key='teks' class="alert border border-secondary alert-dismissible" role="alert">
                            <NuxtLink :to="'/cari-resep/' + teks">
                                <small class='text-primary'>{{ teks }}</small>
                            </NuxtLink>
                            <button @click='hapus(teks)' type="button" class="btn-close shadow-none" data-bs-dismiss="alert" aria-label="Close"></button>
                        </div>
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
            item: []
        }
    },

    methods: {
        hapus(q) {
            let arrHistory = JSON.parse(localStorage.history);
            let filter = arrHistory.filter(x => x !== q);
            localStorage.history = JSON.stringify(filter);

            this.item = [];

            for(let t in filter) {
                this.item.push(filter[t]);
            }
        }
    },

    mounted() {
        this.item = JSON.parse(localStorage.history);
    }
}
</script>
