<template>
  <div>
  <h1 style="font-size: 20px; font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande'">Product {{title}}</h1>
    <div class="product">
    <div>
        <img style="max-width: 200px" alt="product"  :src="image" />
      <p style="font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande'"><b>{{ title }}</b> {{ price}}</p> <br />
      <p class="info-text">{{info}}</p>
    </div>
  
        <FormView  /> 
      </div> 
    </div>   
    
   </template>
   
   <script>
   import data from "@/data";
   import FormView from "@/components/FormView.vue"


   export default {
    name: 'ProductComponent',
    components: {
       FormView
    },
     data() {
       return {
         title: "",
         price: "",
         image: "",
         info: "", 
       }
     },
     mounted() {
       const id = this.$route.params.id;
       const product = data.products.find(product => product.id == id);
       this.title = product.title;
       this.price = product.price;
       this.image = product.image;
       this.info = product.info;
     },
   
     
   }
   </script>
   <style scoped>
  
   .product {
    display:flex;
    justify-content:space-between;
    margin-inline: 100px;
    padding: 16px;
   }
   .info-text {
    max-width: 500px;
    }
   
   @media only screen and (max-width: 750px){
    .product {
      display:flex;
      flex-direction: column;
      justify-content: flex-start;
      margin-inline: 0;
     }
   }

  
   </style>