<template>
<div class="row">
  <div class="col-sm-2 admin-sidebar">
    <div class="nav flex-column nav-pills text-center text-uppercase admin-nav" id="sidebar-admin" role="tablist" aria-orientation="vertical">
      <a class="nav-link active show admin-nav-item admin-sidebar-item"  data-toggle="pill" role="tab" aria-controls="admin-communicate" aria-selected="true">Boletos</a>
      <a class="nav-link admin-nav-item admin-sidebar-item" data-toggle="pill" href="http://localhost:8080/listabuses" role="tab" aria-controls="admin-requests" aria-selected="false">altas y bajas buses</a>
      <a class="nav-link admin-nav-item admin-sidebar-item" data-toggle="pill" href="http://localhost:8080/destinobuses" role="tab" aria-controls="admin-users" aria-selected="false">programar destinos</a>
      <a class="nav-link admin-nav-item admin-sidebar-item" data-toggle="pill" href="http://localhost:8080/historialventas" role="tab" aria-controls="admin-users" aria-selected="false">historial de ventas</a> 
    </div>
  </div>
  <div class="col-sm-12 admin-tabs">
    <ul class="nav nav-tabs admin-nav text-uppercase" role="tablist">
      <li class="nav-item">
        <a class="nav-link admin-nav-item active" data-toggle="tab" role="tab" aria-controls="admin-communicate" aria-selected="true">Communicate</a>
      </li>
    </ul>
  </div>
  <div class="col-sm-10">
    <div class="tab-content">
      <div class="tab-pane fade active show" id="admin-communicate" role="tabpanel" aria-labelledby="admin-communicate-tab">
        <ul class="nav nav-pills nav-fill">
          <li class="nav-item">
            <h4><a class="nav-link admin-header-block">compra de boletos- online</a></h4>
          </li>
        </ul>
        <nav class="navbar">
          <form class="form-inline col-sm-12" v-on:submit.prevent="FiltrarDatos">
            <div class="col-sm-3"><input class="form-control mr-sm-2" type="search" disabled placeholder="tuxtla gutierrez" aria-label="first" style="width: 100%;"></div>
            <div class="col-sm-3">
              <select class="form-control mr-sm-2" v-model="select">
              <option v-for="buses in listaBuses" :value="buses.destination" >{{buses.destination}}</option>
              </select>
            </div>
            <div class="col-sm-3">
              <input type="submit"  class="btn btn-success" value="Filtrar Los datos">
            </div>
            <div class="col-sm-3">
               <input class="form-control" type="time" disabled>
            </div>
          </form>
        </nav>

        <nav class="navbar">
          <form class="form-inline col-sm-12" v-on:submit.prevent>
            <div class="col-sm-3">
              <input type="date" class="form-control" disabled>
            </div>
            <div class="col-sm-3">
              <input type="text" class="form-control" placeholder="destino"   disabled>
            </div>
            <div class="col-sm-3">
              <input type="text" class="form-control" placeholder="clase"   disabled>
            </div>
            <div class="col-sm-3">
              <input type="text" class="form-control" placeholder="precio base"   disabled>
            </div>
          </form>
        </nav>


      </div>
    </div>
  </div>
</div>
</template>

<script>
import axios from 'axios';
export default {  
  data(){
    return{
      listaBuses:[],
      token:'',
      ulr:'https://aexajkl.herokuapp.com/api/v1/',
      select:'',
    }
  },
  mounted(){
    this.getAllBuses();
  },
  methods:{
    getAllBuses:function(){
      this.token=JSON.parse(localStorage.getItem('token'));
      this.header={
        headers:{
          Authorization:"Bearer "+this.token
          }
      }
      axios.get(this.ulr+"user/bus/all",this.header)
      .then(response=>{
        this.listaBuses=response.data.bus;
        console.log(response.data);
      })
      .catch(error=>{
        console.log(error.response)
      })
    },
    FiltrarDatos:function() {
      console.log("Xxxxx "+this.select);
    }

  }


}
</script>



<style >
@media screen and (max-width: 480px) {
    .admin-sidebar{
        display: none;
    }
}

@media screen and (min-width: 480px) {
    .admin-tabs{
        display: none;
    }
}

.admin-sidebar{
    max-width: 13%;
}

#sidebar-admin{
    position: fixed;
}

.admin-sidebar-item{
    padding: 1em;
    border-bottom: 1px solid white;
}

.admin-nav{
    background: #49C2B3;
}

.admin-nav-item{
    color: white;
    font-weight:bold;
}

.admin-nav-item:hover{
    color: white;
    background: #41aea1;
}

.admin-nav-item.active{
    background: #53FFE7 !important;
    color: white !important;
}

.admin-header-block{
   background: #434449;
   color: white !important;
   text-align: left;
    padding: 20px;
    margin-top: 10px;
    margin-bottom: 20px;
    border-color: #ddd;
    border-radius: 4px;
    font-weight: bold;
}

.admin-filter-button{
    background: #78B404;
    color: white !important;
    font-weight: bold;
}

.admin-user-card{
    margin-bottom: 10px;
}

</style>