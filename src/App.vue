<template>
    <div id="app">
        <!--<img alt="Vue logo" src="./assets/logo.png">-->
        <img alt="Vue logo" src="./assets/clickerPNG.png">
        <HelloWorld msg="ほらクリックするんだよ"/>

        <!--TwitterのIDをさらしていくすたいる-->
        <div class="wrapper">
            <footer>
                © 2019 S-YamaguchiC( <a href="https://twitter.com/kawasaki_dst" style="color: black">@kawasaki_dst</a> )
            </footer>
        </div>
    </div>
</template>


<script>
    import HelloWorld from './components/HomePage.vue'

    export default {
        name: 'app',
        components: {
            HelloWorld
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 10px;
    }

    .wrapper{
        height: 100%;
        min-height: 100vh;
        position: relative;/*←相対位置*/
        padding-bottom: 100px;/*←footerの高さ*/
        box-sizing: border-box;/*←全て含めてmin-height:100vhに*/
    }

    footer{
        width: 100%;
        background-color: #87cefa;
        color: #fff;
        text-align: center;
        padding: 10px 0;

        position: absolute;/*←絶対位置*/
        bottom: 0; /*下に固定*/
    }
</style>
