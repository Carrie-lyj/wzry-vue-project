<template>
    <section class='index'>
        <!-- 轮播图start -->
        <v-swipe :swipeList="swipeList"></v-swipe>
        <!-- 轮播图end -->
    </section>
</template>

<script>
import mSwiper from '../swipe/swipe.vue';
import config from '../../js/config.js';

export default {
    data() {
        return {
            'swipeList': []
        }
    },
    methods: {
        getLunbo() {
            let url = config.getHomeLunbo;
            this.$http.get(url).then(rep => {
                let body = rep.body;
                if (body.status == 0) {
                    console.log(this);
                    this.swipeList = body.message;
                    console.log(this.swipeList);
                }
            });
        }
    },
    components: {
        'v-swipe': mSwiper
    },
    created() {
        this.getLunbo();
    }
}
</script>

<style>

</style>

