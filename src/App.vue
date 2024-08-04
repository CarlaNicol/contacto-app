<template>
  <div id="app">
    <router-view :contacts="contacts" @add-contact="addContact" @edit-contact="editContact" @delete-contact="deleteContact"></router-view>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contacts: [
        { id: 1, name: "Alice Johnson", 
        email: "alice.johnson@example.com", 
        address: "123 Maple Street", 
        phone: "123-456-7890", 
        country: "USA", 
        city: "New York" },
        { id: 2, name: "Bob Smith", 
        email: "bob.smith@example.com", 
        address: "456 Oak Avenue", 
        phone: "987-654-3210", 
        country: "Canada", 
        city: "Toronto" },
        {
        id: 3,
        name: "Carol White",
        email: "carol.white@example.com",
        address: "789 Pine Road",
        phone: "555-123-4567",
        country: "UK",
        city: "London"
        },
        {
        id: 4,
        name: "David Brown",
        email: "david.brown@example.com",
        address: "321 Elm Street",
        phone: "444-555-6666",
        country: "Australia",
        city: "Sydney"
        },
        {
        id: 5,
        name: "Emily Davis",
        email: "emily.davis@example.com",
        address: "654 Spruce Lane",
        phone: "333-444-5555",
        country: "USA",
        city: "Los Angeles"
        }
        // más contactos...
      ]
    }
  },
  methods: {
    addContact(newContact) {
      newContact.id = this.contacts.length > 0 ? this.contacts[this.contacts.length - 1].id + 1 : 1;
      this.contacts.push(newContact);
    },
    editContact(updatedContact) {
      const index = this.contacts.findIndex(contact => contact.id === updatedContact.id);
      if (index !== -1) {
        this.contacts.splice(index, 1, updatedContact);
      }
    },
    deleteContact(id) {
      this.contacts = this.contacts.filter(contact => contact.id !== id);
    }
  }
}
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: hwb(0 98% 1%);
  margin: 0;
  padding: 0;
}


</style>
