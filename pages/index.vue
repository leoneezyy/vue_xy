<template>
    <div class="container">
        <!-- 轮播图 -->
        <!-- interval: 相隔时间 -->
        <!-- arrow: 是否显示左右的箭头 -->

        <el-carousel :interval="5000" arrow="always">
            <el-carousel-item v-for="(item, index) in banners" :key="index">
                <div
                    class="banner-image"
                    :style="`
                    background:url(${$axios.defaults.baseURL + item.url}) center center no-repeat;
                    background-size:contain contain;
                    `"
                ></div>
            </el-carousel-item>
        </el-carousel>
    </div>
</template>

<script>
export default {
    data() {
        return {
            banners: []
        };
    },

    async mounted() {
        // 返回一个promise,res就是axios的resolve的参数（也就是.then的回调函数的参数）
        const res = await this.$axios({
            url: '/scenics/banners'
        });

        const {data} = res.data
        this.banners = data
    }
};
</script>

<style lang="less" scoped>
.container {
    min-width: 1000px;
    margin: 0 auto;
    position: relative;

    /deep/ .el-carousel__container {
        height: 700px;
    }

    .banner-image {
        width: 100%;
        height: 100%;
    }
}
</style>