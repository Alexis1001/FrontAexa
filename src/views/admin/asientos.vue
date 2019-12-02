<template>
<div class="container">
<table class="table table-striped custab">
  <tbody>
    <tr v-for="(bus,index) in  30 " v-bind:key="index">
      <th scope="row">index</th>
      <td><button>hola</button></td>
      <td>Otto</td>
      <td>@mdo</td>
    </tr>
  </tbody>
</table>
    
</div>
 
</template>

<script>
export default {
    data(){
        return{
            boleto:[],
        }
    },
    mounted(){
        this.start();
    },
    methods:{
        start:function(){
            this.boleto=JSON.parse(localStorage.getItem('boleto'));
            console.log(this.boleto[0].nombre)
        }
    }   
    
}
</script>


<style>


</style>

