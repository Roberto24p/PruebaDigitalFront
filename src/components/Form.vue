<template>
  <div class="column">
    <button class="button" v-on:click="active = true">{{ bttText }}</button>
  </div>
  <div v-bind:class="{ 'is-active': active }" class="modal">
    <div class="modal-background" v-on:click="active = false"></div>
    <div class="modal-content column is-4">
      <div class="box">
        <form class="">
          <div class="field">
            <label class="label">Nombre</label>
            <div class="control has-icons-left has-icons-right">
              <input
                class="input is-success"
                type="text"
                placeholder="Nombre"
                v-model="nombre"
              />
              <span class="icon is-small is-left">
                <i class="fas fa-user"></i>
              </span>
              <span class="icon is-small is-right">
                <i class="fas fa-check"></i>
              </span>
            </div>
          </div>

          <div class="field">
            <label class="label">Telefono</label>
            <div class="control has-icons-left has-icons-right">
              <input
                class="input is-success"
                type="text"
                placeholder="Telefono"
                v-model="telefono"
              />
              <span class="icon is-small is-left">
                <i class="fas fa-user"></i>
              </span>
              <span class="icon is-small is-right">
                <i class="fas fa-check"></i>
              </span>
            </div>
          </div>

          <div class="field">
            <label class="label">Contraseña</label>
            <div class="control has-icons-left has-icons-right">
              <input
                class="input is-success"
                type="password"
                placeholder="Contraseña"
                v-model="password"
              />
              <span class="icon is-small is-left">
                <i class="fas fa-user"></i>
              </span>
              <span class="icon is-small is-right">
                <i class="fas fa-check"></i>
              </span>
            </div>
          </div>
          <div class="field">
            <label class="label">Fecha de Nacimiento</label>
            <div class="control has-icons-left has-icons-right">
              <input
                class="input is-success"
                placeholder="Text input"
                type="date"
                step="1"
                v-model="fechaNacimiento"
              />
              <span class="icon is-small is-left">
                <i class="fas fa-user"></i>
              </span>
              <span class="icon is-small is-right">
                <i class="fas fa-check"></i>
              </span>
            </div>
          </div>
          <div class="field">
            <div class="control">
              <label class="radio" v-for="item in roles" :key="item.cod_permiso">
                -{{item.nombre}}
              </label>
            </div>
          </div>
          
          <div class="field">
            <label class="label">Estado</label>
            <div class="control">
              <div class="select">
                <select v-model="state">
                  <option>A</option>
                  <option>I</option>
                  <option>E</option>
                </select>
              </div>
            </div>
          </div>
          <div class="field is-grouped">
            <div class="control">
              <button class="button is-warning" v-on:click="sendData">
                Submit
              </button>
            </div>
            <div class="control">
              <button class="button is-danger is-light">Cancel</button>
            </div>
          </div>
        </form>
      </div>
    </div>

    <button
      class="modal-close is-large"
      aria-label="close"
      v-on:click="active = false"
    ></button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      nombre: this.propNombre,
      telefono: this.propTelefono,
      password: "",
      fechaNacimiento: this.propFechaNacimiento,
      active: false,
      state: this.propEstado,
      roles: []
    };
  },
  props: {
    propNombre: String,
    propTelefono: String,
    propFechaNacimiento: String,
    bttText: String,
    propPassword: String,
    propEstado: String,
    propId: String,
  },
  mounted() {
    fetch('http://localhost/testApi/public/usuarioPermiso/'+this.propId)
      .then(result => result.json())
      .then(data => this.roles = data)
  },
  methods: {
    sendData() {
 
      if (this.bttText == "Add") {
        const person = {
          nombre: this.nombre,
          telefono: this.telefono,
          password: this.password,
          fechaNac: this.fechaNacimiento,
        };
        const obj = {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(person),
        };
        console.log(person);
        fetch("http://localhost/testApi/public/usuario", obj)
          .then((result) => result.json())
          .then((data) => console.log(data));
      } else {
        const person = {
          nombre: this.nombre,
          telefono: this.telefono,
          password: this.password,
          fechaNac: this.fechaNacimiento,
          estado: this.state,
          id: this.propId,
        };
        const obj = {
          method: "PUT",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(person),
        };
        fetch("http://localhost/testApi/public/usuario", obj)
          .then((result) => result.json())
          .then((data) => console.log(data));
      }
    },
  },
};
</script>
