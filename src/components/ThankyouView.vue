
<template>
    <div class="modal-container">  
    <div class="modal">
        <div class="info">
            <h1 class="thankYou">Thank you for your order!!</h1>
       
        <p><strong>Product:</strong> {{title}}</p><br/>
        <p><strong>Price:</strong> {{price}}</p><br/>
        <p class="info-text"><strong>Information:</strong> {{info}}</p><br/>
        </div>
        <div>
            <button>
            <router-link
        :to="{ name: 'home'}">
       Back to products
      </router-link> 
    </button>
        </div>

    </div>
</div>

</template>
<script>
   import data from "@/data";
export default {

    data() {
       return {
         title: "",
         price: "",
         info: "", 
       }
     },
     mounted() {
       const id = this.$route.params.id;
       const product = data.products.find(product => product.id == id);
       this.title = product.title;
       this.price = product.price;
       this.info = product.info;
     },
}
</script>
<style scoped>
  .thankYou {
    white-space: nowrap;
    font-size: 20px; 
    font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande';
  }
  .info {
    display:flex;
    flex-direction: column;
    align-items: flex-start;
    font-size: 12px;  
  }
  button {
    margin-top: 250px;
  }
 
.modal-container {
    display: flex; 
    align-items: center;
    justify-content: center;
}
.modal {
    display: flex;
    width: 500px;
    justify-content: space-between;
    padding: 30px;
    background-color: #ebeaea;
}
.info-text {
  display: block;
  max-width: 300px;
  overflow: hidden;
  white-space:nowrap;
  text-overflow: ellipsis;
}
@media only screen and (max-width: 750px){
  .modal {
    display: flex;
    justify-content: center;
  }
  .info {
    max-width: 220px;
  }
}
</style>
