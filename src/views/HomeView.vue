<template>
  <div class="container">
    <h1 class="title">Agenda de contactos</h1>
    <div class="filter-container">
      <input v-model="search" placeholder="Filtro" class="filter-input"/>
      <button @click="navigateToAdd" class="add-button">Agregar</button>
    </div>
    <table class="contact-table">
      <thead>
        <tr>
          <th>ID</th>
          <th>Nombre</th>
          <th>Email</th>
          <th>Dirección</th>
          <th>Teléfono</th>
          <th>País</th>
          <th>Ciudad</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="contact in filteredContacts" :key="contact.id">
          <td>{{ contact.id }}</td>
          <td>{{ contact.name }}</td>
          <td>{{ contact.email }}</td>
          <td>{{ contact.address }}</td>
          <td>{{ contact.phone }}</td>
          <td>{{ contact.country }}</td>
          <td>{{ contact.city }}</td>
          <td>
            <button @click="navigateToEdit(contact.id)" class="edit-button">Editar</button>
            <button @click="deleteContact(contact.id)" class="delete-button">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    contacts: Array
  },
  data() {
    return {
      search: ''
    }
  },
  computed: {
    filteredContacts() {
      return this.contacts.filter(contact => 
        contact.name.toLowerCase().includes(this.search.toLowerCase()) ||
        contact.email.toLowerCase().includes(this.search.toLowerCase())
      );
    }
  },
  methods: {
    navigateToAdd() {
      this.$router.push({ name: 'add-contact' });
    },
    navigateToEdit(id) {
      this.$router.push({ name: 'edit-contact', params: { id } });
    },
    deleteContact(id) {
      this.$emit('delete-contact', id);
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 1000px;
  margin: 50px auto;
  padding: 20px;
  background: #fff;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.title {
  font-size: 24px;
  color: #333;
  margin-bottom: 10px; /* Reduce el margen inferior */
}

.filter-container {
  display: flex;
  align-items: center;
  margin-bottom: 10px; /* Reduce el margen inferior */
}

.filter-input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  margin-right: 10px; /* Añade espacio entre el input y el botón */
}

.add-button {
  padding: 10px 15px;
  background-color: #28a745;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.add-button:hover {
  background-color: #218838;
}

.contact-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px; /* Reduce el margen superior */
  border: 1px solid #ddd; /* Borde alrededor de la tabla */
}

.contact-table th, .contact-table td {
  border: 1px solid #ddd; /* Borde alrededor de cada celda */
  padding: 8px;
  text-align: left;
}

.contact-table th {
  background-color: #f4f4f4;
}

.edit-button, .delete-button {
  padding: 5px 10px;
  margin: 5px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.edit-button {
  background-color: #007bff;
  color: white;
}

.edit-button:hover {
  background-color: #0056b3;
}

.delete-button {
  background-color: #dc3545;
  color: white;
}

.delete-button:hover {
  background-color: #c82333;
}
</style>
