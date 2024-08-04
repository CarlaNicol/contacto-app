<template>
    <div>
      <h1>Agregar Contacto</h1>
      <form @submit.prevent="addContact">
        <div class="form-group">
          <label for="name">Nombre</label>
          <input id="name" v-model="contact.name" placeholder="Nombre" required />
        </div>
        <div class="form-group">
          <label for="email">Correo</label>
          <input id="email" v-model="contact.email" placeholder="Correo" required />
        </div>
        <div class="form-group">
          <label for="address">Dirección</label>
          <input id="address" v-model="contact.address" placeholder="Dirección" required />
        </div>
        <div class="form-group">
          <label for="phone">Teléfono</label>
          <input id="phone" v-model="contact.phone" placeholder="Teléfono" required />
        </div>
        <div class="form-group">
          <label for="country">País</label>
          <input id="country" v-model="contact.country" placeholder="País" required />
        </div>
        <div class="form-group">
          <label for="city">Ciudad</label>
          <input id="city" v-model="contact.city" placeholder="Ciudad" required />
        </div>
        <button type="submit">Agregar</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        contact: {
          name: '',
          email: '',
          address: '',
          phone: '',
          country: '',
          city: ''
        }
      }
    },
    methods: {
      addContact() {
        const newContact = { ...this.contact, id: Date.now() };
        this.$emit('add-contact', newContact);
        this.$router.push('/');
      }
    }
  }
  </script>
  
  <style scoped>
  .form-group {
    margin-bottom: 15px;
  }
  
  .form-group label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }
  
  .form-group input {
    width: calc(100% - 22px);
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }
  
  button {
    padding: 10px 15px;
    margin-top: 10px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #218838;
  }
  </style>
  