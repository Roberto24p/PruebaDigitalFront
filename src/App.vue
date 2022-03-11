<template>
  <div class="container">
    <h1>CRUD</h1>

      <Form bttText='Add'></Form>
  <Content></Content>
  </div>
</template>

<script>
import Form from "@/components/Form";
import Content from '@/components/Content'
import "bulma/css/bulma.css";

export default {
  name: "App",
  components: {
    Form,
    Content
  },
};
</script>

<style>
.container{
  margin: auto;

  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
