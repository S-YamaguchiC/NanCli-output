<template>
    <div class="hello">
        <h1>{{ msg }}</h1>

        <form id="n_form">
            <p>選択肢 → [
                <input type="radio" name="b1" value="A" @click="addData" required>A
                <input type="radio" name="b1" value="B" @click="addData" required>B
                <input type="radio" name="b1" value="C" @click="addData" required>C
                <input type="radio" name="b1" value="D" @click="addData" required>D
                 ]
            </p>
        </form>

        <h3>↓結果だお↓</h3>
        <div class="small">
            <line-chart :chart-data="datacollection" style="width: 450px;"></line-chart>
        </div>

        <!--TwitterのIDをさらしていくすたいる-->
        <div class="wrapper">
            <footer>
                Created by ちくわまんじ（ @kawasaki_dst ）
            </footer>
        </div>

    </div>
</template>

<script>
    // Vue.component('chart-comp', PieChart)
    import LineChart from './PieChart.js'

    export default {
        components: {
            LineChart
        },
        data () {
            return {
                counterA: 1,
                counterB: 1,
                counterC: 1,
                counterD: 1,
                datacollection: null
            }
        },
        mounted () {
            this.fillData()
        },
        methods: {
            fillData () {
                this.datacollection = {
                    labels: ['A:' + this.counterA, 'B:' + this.counterB, 'C:' + this.counterC, 'D:' + this.counterD],
                    datasets: [
                        {
                            label: ['A', 'B', 'C', 'D'],
                            backgroundColor: ['#f87979', '#f27732', '#f12735', '#f34628'],
                            data: [this.counterA, this.counterB, this.counterC, this.counterD]
                        }
                    ]
                }
            },

            addData: function () {
                // ラジオボタン選んでSubmit押した時の円グラフ更新
                var radio = document.getElementById('n_form').b1.value

                // 押されたラジオボタンでそれぞれいんくりめんと
                if (radio === "A") {
                    this.counterA++
                    this.fillData()
                } else if (radio === "B") {
                    this.counterB++
                    this.fillData()
                } else if (radio === "C") {
                    this.counterC++
                    this.fillData()
                } else if (radio === "D") {
                    this.counterD++
                    this.fillData()
                } else {
                    alert("err")
                }

                // ラジオボタンと送信ボタンを無効化する(reset呼び出しで有効化)
            },
            reset: function () {
                // ボタンを押したら、投票を無効にしてラジオボタンを初期化
            }
        }
    }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
        max-width: 450px;
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
        background-color: #FA8258;
        color: #fff;
        text-align: center;
        padding: 10px 0;

        position: absolute;/*←絶対位置*/
        bottom: 0; /*下に固定*/
    }
</style>
