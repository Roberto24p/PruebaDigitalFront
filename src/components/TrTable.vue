<template>
  <tr>
    <td>{{nombre}}</td>
    <td>{{telefono}}</td>
    <td>{{fechaNacimiento}}</td>
    <td>{{estado}}</td>
    <td><Form bttText='Editar' :propNombre='nombre' :propTelefono='telefono' :propFechaNaimiento='fechaNacimiento' :propEstado='estado' :propId='idItem'></Form></td>
     <td><button class="button is-danger"> Eliminar</button></td>
  </tr>
</template>

<script>
import Form from "@/components/Form";
export default {
  components:{
    Form
  },
    props: ['nombre', 'telefono', 'fechaNacimiento', 'estado', 'idItem']
}
</script>

<style>

</style>