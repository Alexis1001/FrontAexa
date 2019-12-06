<template>
<!--<div class="container">
<table class="table table-striped custab">
  <tbody>
    <tr v-for="(bus,index) in 5" v-bind:key="index">
      <th scope="row">index</th>
      <td><button>hola</button></td>
      <td>Otto</td>
      <td>@mdo</td>
    </tr>
  </tbody>
</table>
    
</div>-->
<div>
  <div class="row" v-for="(bus,index) in 5" v-bind:key="index">

    <div class="col-lg-1">
      <button class="btn btn-primary">{{index}}</button>
    </div>
    <div class="col-lg-1">
      <button class="btn btn-primary">{{index}}</button>
    </div>
    <div class="col-lg-1">
      <button class="btn btn-primary">{{index}}</button>
    </div>
    <div class="col-lg-1">
      <button class="btn btn-primary">{{index}}</button>
    </div>
  </div>
</div>



</template>

<script>
export default {
    data(){
        return{
            boleto:[],
            id:'',
            ulr:'https://aexajkl.herokuapp.com/api/v1/',
        }
    },
    mounted(){
        this.start();
    },
    methods:{
        start:function(){
            ///this.token=JSON.parse(localStorage.getItem('token'));
            //this.boleto=JSON.parse(localStorage.getItem('boleto'));
            //this.id=this.boleto[0].id;
            //console.log("id del bus "+this.id);
            //console.log("token "+this.token);
        },
        getBusId:function(){

          /*axios.get(this.ulr+"user/bus/"+this.id)
          .then(error=>{

          })
          .catch(error=>{

          })*/

        }

    }   
    
}
</script>


<style>


</style>

