<template>
    <div>
      <h1>List</h1>
      <ul>
        <!-- API로부터 받아온 데이터를 리스트로 표시 -->
        <li v-for="row in list" :key="row.item_id">
          {{ row.item_name }}
        </li>
      </ul>
    </div>
  </template>

  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        list: [], // 데이터를 저장할 배열
      };
    },
    mounted() {
      this.fetchData(); // 컴포넌트가 마운트되면 데이터를 가져옴
    },
    name: 'GersangItem',
    methods: {
      async fetchData() {
        try {
          // RESTful API로부터 데이터를 가져옴
          const response = await axios.get('http://3.38.169.9:3000/api/items');
          this.list = response.data; // 가져온 데이터를 posts 배열에 저장
        } catch (error) {
          console.error('There was an error fetching the data:', error);
        }
      },
    },
  };
  </script>