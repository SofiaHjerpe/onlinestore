<template>
    <div>
        <div class="products" v-for="i in products" :key="i">
            <div class="product-data">
            <img class="product-image" alt="product" :src="i.image" />
        
            <span class="product-info">
              <p><b>{{i.title}} </b></p> <br/>
              <p>{{i.price}}</p>
            </span>
          </div>
          <div>

       <button>
        <router-link
        :to="{ name: 'product', params: { id: i.id }}">
        Buy Product
      </router-link> 
       </button>
      </div>
      </div>
     </div>
</template>
<script>
 import data from "@/data.js";
 export default {
   data() {
     console.log(data);
     return {
       products: data.products
     }
   },
   mounted() {
     console.log(data);
   }, 
   
 }
</script>
<style scoped>
.products {
  display: flex; 
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin: 16px;
  border-bottom: 2px solid #42b9836e;
  padding: 0;
}
.product-image {
  max-width: 300px;
  padding: 16px
}
.product-data{
  display:flex;
  flex-direction:row;
  align-items:center;
  flex-flow: nowrap;
}
.product-info {
  display: flex; 
  justify-content: center;
  gap: 10px;
  flex-flow: nowrap;
  font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande';
}
@media only screen and (max-width: 800px){
  .products {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    padding: 16px;
  }
  .product-data{
    display: flex;
    flex-direction: column;
  }
  .product-info{
    display:flex; 
    flex-direction: column;
    flex-flow: wrap;
  }
  .product-image {
    max-width: 200px;
    padding: 16px
  }
}



</style>