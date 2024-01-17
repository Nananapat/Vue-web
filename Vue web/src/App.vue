<template>
  <div id="app">
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
    <MasterTable :owners="owners" />
  </div>
</template>

<script>
import MasterTable from './components/MasterTable.vue';

export default {
  components: {
    MasterTable,
  },

  data() {
    return {
      owners: [
        { hn: '002530', name: 'มิท บุญเจริญ', phone: '0946236355', email: 'ztar' },
        { hn: '002512', name: 'ZACH PATZIG', phone: '0930914384', email: 'zpatzig@gmail.com' },
        { hn: '002549', name: 'ทศพล วิริยะ อาชา', phone: '0885710057', email: '3ucx@hotmail.com' },
        { hn: '000424', name: 'ขวัญ อาภรณ์ อาจ ท', phone: '0884959191', email: 'zongkubb@gmail.com' },
        { hn: '000093', name: 'รตนวรรณ จินดาภ', phone: '0885522602', email: 'zippyclosed@gmail.com' },
      ],
      pageSize: 20,
      currentPage: 1,
      totalPages: 29,
      hnList: ['002530', '002512', '002549', '000424', '000093'],
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 6px solid rgb(0, 146, 0);
}

.table-container {
  margin-top: 20px; 
  overflow-x: auto; 
}

table {
  width: 100%;
  border-collapse: collapse;
}

table th, table td {
  border: 1px solid black;
  padding: 8px;
  text-align: left;
}

table th {
  background-color: #b9b9b9;
}

table td i {
  font-size: 16px;
  color: #f44242; 
}

.selected i {
  color: #2ecc71; 
}
</style>