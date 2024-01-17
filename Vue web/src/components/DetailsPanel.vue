<template>
  <div class="container">
    <div class="header">
      <div class="title">ข้อมูลผู้ติดต่อ</div>
      <div class="actions">
        <button class="cancel-button" @click="cancel">Cancel</button>
        <button class="save-button" @click="saveContact">Save</button>
        <button class="delete-button" @click="deleteContact">Delete</button>
      </div>
    </div>
    <div class="content">
      <div class="hn-field">
        <label for="hn">HN</label>
        <input type="text" id="hn" v-model="editedContact.hn">
      </div>
      <div class="firstname-field">
        <label for="firstname">ชื่อ</label>
        <input type="text" id="firstname" v-model="editedContact.name">
      </div>
      <div class="phone-field">
        <label for="phone">เบอร์มือถือ</label>
        <input type="tel" id="phone" v-model="editedContact.phone">
      </div>
      <div class="email-field">
        <label for="email">Email</label>
        <input type="email" id="email" v-model="editedContact.email">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    contact: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      editedContact: { ...this.contact },
    };
  },
  methods: {
    cancel() {
      this.$emit('cancel');
    },
    saveContact() {
      this.$emit('update-contact', this.editedContact);
    },
    deleteContact() {
      this.$emit('delete-contact');
    },
  },
};
</script>

<style>

.container {
  width: 400px; 
  margin: 0 auto; 
  padding: 20px;
  border: 1px solid #ccc; 
  border-radius: 5px; 
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); 
}


.header {
  display: flex;
  justify-content: space-between; 
  align-items: center; 
  margin-bottom: 20px;
}

.title {
  font-size: 18px; 
  font-weight: bold;
}

.actions {
  display: flex;
  gap: 10px; 
}


.cancel-button,
.save-button,
.delete-button {
  background-color: #f0f0f0; 
  border: none;
  padding: 8px 12px;
  border-radius: 5px;
  font-size: 14px;
  cursor: pointer;
}


.cancel-button:hover {
  background-color: #e0e0e0;
}

.save-button:hover {
  background-color: #09b109;
}

.delete-button:hover {
  background-color: #c50a0a;
}


.content {
  display: flex;
  flex-direction: column;
  gap: 15px; 
}


.hn-field,
.firstname-field,
.phone-field,
.email-field {
  display: flex;
  align-items: center;
}

label {
  width: 100px; 
  margin-right: 10px;
}

input {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 5px;
}

</style>
