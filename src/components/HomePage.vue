<template>
    <div class="hello">
        <h1>{{ msg }}</h1>

        <div class="small">

            <h3>↓結果だお↓</h3>
            <line-chart :chart-data="datacollection" style="width: 350px;"></line-chart>
        </div>

        <p>リセットボタン</p>
        <form id="reset_form">
            <input type="button" @click="reset" value="チャートを初期化"/>
        </form>

        <!--TwitterのIDをさらしていくすたいる-->
        <div class="wrapper">
            <footer>
                © 2019 S-YamaguchiC( <a href="https://twitter.com/kawasaki_dst" style="color: black">@kawasaki_dst</a> )
            </footer>
        </div>

    </div>
</template>

<script>
    // Vue.component('chart-comp', PieChart)
    import LineChart from './PieChart.js'
    import axios from 'axios'

    export default {
        components: {
            LineChart
        },
        data () {
            return {
                // 初期値
                counterA: 1,
                counterB: 1,
                counterC: 1,
                counterD: 1,
                datacollection: null
            }
        },
        mounted () {
            this.fillData()
            this.reDraw()
        },

        // 以下で関数を定義
        methods: {

            // チャート描画用
            fillData () {

                // axiosでとってくる
                axios.get('CGIのパス')
                    .then(response => {
                        this.counterA = response.data.counterA
                        this.counterB = "cgiのでーた"
                        this.counterC = "cgiのでーた"
                        this.counterD = "cgiのでーた"
                    })
                    .catch(err => {
                        this.counterA = err
                        this.counterB = "cgiのでーた"
                        this.counterC = "cgiのでーた"
                        this.counterD = "cgiのでーた"
                    });

                this.datacollection = {
                    labels: ['A', 'B', 'C', 'D'],
                    datasets: [
                        {
                            label: ['A', 'B', 'C', 'D'],
                            backgroundColor: ['#5f9ea0', '#eee8aa', '#ffa07a', '#dda0dd'],
                            data: [this.counterA, this.counterB, this.counterC, this.counterD]
                            // data: [ method1(), method2(), method3(), method4() ]
                        }
                    ]
                }
            },

            // チャートを初期化する
            reset: function () {
                alert("RESET")
                // ボタンを押したら、投票を無効にしてラジオボタンを初期化
                this.counterA = 1
                this.counterB = 1
                this.counterC = 1
                this.counterD = 1
                // this.form.submit()
            },

            // 定期実行
            reDraw:function () {
                this.fillData().interval(10000)
            }
        }
    }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .hello {
        alignment: center;
    }
    h3 {
        margin: 40px 0 0;
    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        display: inline-block;
        margin: 0 10px;
    }
    a {
        color: #42b983;
    }
    .small {
        max-width: 400px;
        margin:  25px auto;
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
