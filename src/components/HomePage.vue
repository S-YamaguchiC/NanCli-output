<template>
    <div class="hello">

        <div class="small">

            <h3>↓結果だお↓</h3>
            <line-chart :chart-data="datacollection" style="width: 350px;"></line-chart>

            <input type="button" @click="fillData()" value="更新ボタン">
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
                counterA: 0,
                counterB: 0,
                counterC: 0,
                counterD: 0,
                datacollection: {}, // ここをnullにすると、console上でエラーになる
                // object: null
            }
        },
        mounted () {
            this.fillData()
        },

        // 以下で関数を定義
        methods: {

            // チャート描画用
            fillData () {
                // axiosでとってくる
                axios.post('ここにURL')
                    .then(response => {
                        console.log(JSON.parse(response.status))
                        this.counterA = JSON.stringify(response.data.vote['1'])
                        this.counterB = JSON.stringify(response.data.vote['2'])
                        this.counterC = JSON.stringify(response.data.vote['3'])
                        this.counterD = JSON.stringify(response.data.vote['4'])
                        console.log(this.counterA, this.counterB, this.counterC, this.counterD)
                    })
                    .catch(err => {
                        var object = JSON.parse(err.status)
                        console.log(object)
                    });

                this.datacollection = {
                    labels: ['1', '2', '3', '4'],
                    datasets: [
                        {
                            label: ['1', '2', '3', '4'],
                            backgroundColor: ['#5f9ea0', '#eee8aa', '#ffa07a', '#dda0dd'],
                            data: [this.counterA, this.counterB, this.counterC, this.counterD]
                            // data: [ method1(), method2(), method3(), method4() ]
                        }
                    ]
                }
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

</style>
