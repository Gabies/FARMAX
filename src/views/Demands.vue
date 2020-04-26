<template>
    <div>
        <div class="row">
            <div class="teal lighten-2 col s12 m3">
                <p>INDEX AND COST ESTIMATION</p>
                <hr>
                
                <table>
                    <thead>
                        <tr>
                            <th>PRODUCT</th>
                            <th>Q.D</th>
                            <th>PRICE</th>
                        </tr>
                    </thead>

                    <tbody>
                        <tr v-for="prod in products" :key="prod.id">
                            <td>{{prod.title}}</td>
                            <td>150</td>
                            <td>${{prod.price}}</td>
                        </tr>
                        
                    </tbody>
                </table>
                
            </div>

            <div class="deep-orange lighten-4 col s12 m9 ">
                <h2 class="green-text text-darken-2">DEMANDS</h2>
                <bar-chart
                                    id="donut"
                                    :data="barData"
                                    :xkey="xkeys"
                                    :ykeys="ykeys"
                                    barColors='[ "#FF6384", "#36A2EB", "#FFCE56" ]'
                                    resize="true">
                </bar-chart>

            </div>
        </div>
    </div>
</template>


<script>
import { BarChart } from 'vue-morris'
export default {  
    data(){
        return {
            months: "April",
            days:[1,2,3,4,5,6,7,8,9,10],
            products:[
                {id:1,title:"PRODUCT1",description:"Lorem LoremLoremLoremLorem",price:300},
                {id:2,title:"PRODUCT2",description:"Lorem LoremLoremLoremLorem",price:100},
                {id:3,title:"PRODUCT3",description:"Lorem LoremLoremLoremLorem",price:50},
                {id:4,title:"PRODUCT4",description:"Lorem LoremLoremLoremLorem",price:20}
            ],
            barData: [
                {label:'Product1', value: 300 },
                {label:'Product2', value: 50 },
                {label:'Product3', value: 100 }
                ],
            ykeys: ['value'],
            xkeys:'label'
        }
    },components:{
        BarChart
    },
    mounted(){
        let products=[]
        this.products.forEach(prod=>{
            products.push({label:prod.title,value:prod.price})
        })
        this.barData=products
    }
    
}
</script>

<style >
body{
    line-height: 40px;
}
    hr{
        border: 2px solid;
        color: #9ccc65;
    }
.bold{
      font-weight: bold;
}
</style>