<template>
<div>
<br>
    <h1> Category  List </h1>
   
     <b-table striped hover
      :items="categories" 
      :fields="fields"
      :per-page="pageSize"
      :current-page="pageIndex"></b-table>
        <b-pagination  size="md" :total-rows="categories.length" v-model="pageIndex" :per-page="pageSize">
      </b-pagination>
    </div>
</template>


<script>
import axios from "axios";

export default {
  name: "categories",

  data() {
    return {
      message: "category",
     categories: [],
      pageSize: 10,
      pageIndex: 1,
      fields: [
        {
          key: "category_id",
          sortable: true,
          variant: "warning"
        },
        {
          key: "category_name",
          sortable: true,
          variant: "success"
        },

        {
          key: "description",
          sortable: true,
          variant: "danger"
        }
        

        
      ]
    };
  },
  mounted() {
    var instance = this;
    axios
      .get("https://peaceful-wave-72681.herokuapp.com/api/categories/") //ต้องเอามาใส่
      .then(function(response) {
        console.log(response.data);
        instance.categories = response.data.data;
      });
  }
};
</script>
