<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th><abbr title="Position">Nombre</abbr></th>
          <th>Telefono</th>
          <th>Fecha de Nacimiento</th>
          <th>Estado</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <TrTable v-for="item in listData" :key='item.cod_usuario' :idItem='item.cod_usuario' :nombre='item.nombre' :telefono='item.telefono' :fechaNacimiento='item.fecha_nacimiento' :estado='item.estado' >

        </TrTable>
      </tbody>
    </table>
  </div>
</template>

<script>
import TrTable from '@/components/TrTable'
export default {
  components:{
    TrTable
  },
  data(){
    return{
     listData: []
    }
  },
  methods:{

  },
  mounted(){
    fetch('http://localhost/testApi/public/usuario')
      .then(response=> response.json())
      .then(data=>{console.log(data);this.listData = data})
  }
};
</script>
