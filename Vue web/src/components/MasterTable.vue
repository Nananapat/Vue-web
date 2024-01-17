<template>
  <div>
    <h1>ค้นหาเจ้าของ</h1>
    <table>
      <thead>
        <tr>
          <th>opereter</th>
          <th>HN เจ้าของ</th>
          <th>ชื่อเจ้าของ</th>
          <th>เบอร์ติดต่อ</th>
          <th>อีเมลล์</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(owner, index) in localOwners" :key="index" @click="showDetails(owner)">
          <td ><i class="material-icons">attachment</i></td>
          <td>{{ owner.hn }}</td>
          <td>{{ owner.name }}</td>
          <td>{{ owner.phone }}</td>
          <td>{{ owner.email }}</td>
        </tr>
      </tbody>
    </table>
    <DetailsPanel v-if="selectedRowIndex !== -1" :contact="localOwners[selectedRowIndex]" @close-details="closeDetails" @update-contact="updateContact" />
  </div>
  <button @click="addContact">เพิ่มข้อมูลติดต่อ</button>
</template>

<script>
import DetailsPanel from '@/components/DetailsPanel.vue';

export default {
  components: {
    DetailsPanel,
  },
  props: {
    owners: Array,
  },
  data() {
    return {
      selectedRowIndex: -1,
      localOwners: [],
    };
  },
  watch: {
    owners: {
      immediate: true,
      handler(newOwners) {
        this.localOwners = newOwners.slice();
      },
    },
  },
  methods: {
    showDetails(owner) {
      this.selectedRowIndex = this.localOwners.indexOf(owner);
    },
    closeDetails() {
      this.selectedRowIndex = -1;
    },
    addContact() {
      this.selectedRowIndex = -1;
      const newContact = { hn: '', name: '', phone: '', email: '' };
      this.localOwners.push(newContact);
      this.showDetails(newContact);
    },
    updateContact(updatedContact) {
      if (this.selectedRowIndex !== -1) {
      this.localOwners[this.selectedRowIndex] = updatedContact;
     }
    },
    deleteContact() {
      if (this.selectedRowIndex !== -1) {
        const deletedContact = this.localOwners.splice(this.selectedRowIndex, 1)[0];
        this.selectedRowIndex = -1;
        this.$emit('deleteContact', deletedContact);
      }
    },
  },
};
</script>
