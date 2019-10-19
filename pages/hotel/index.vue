<template>
    <div>
        <div>高德地图</div>
        <div id="container"></div>
    </div>
</template>

<script>
export default {
    mounted() {
        window.onLoad = function() {
            var map = new AMap.Map("container", {
                pitch: 75, // 地图俯仰角度，有效范围 0 度- 83 度
                viewMode: "3D" // 地图模式
            });
        };
        var url =
            "https://webapi.amap.com/maps?v=1.4.15&key=e6d65573f4ddfe52ca6fa3db96433b59&callback=onLoad";
        var jsapi = document.createElement("script");
        jsapi.charset = "utf-8";
        jsapi.src = url;
        document.head.appendChild(jsapi);
    }
};
</script>

<style scoped>
#container {
    width: 500px;
    height: 500px;
    margin: 0px auto;
}
</style>