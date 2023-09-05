<script setup>
import {ref, watch, onMounted} from 'vue'
import router from '@/router';

const fname = ref('')
const lname = ref('')
const cnumber= ref('')
const err = ref('')


watch(fname, (newVal) => {
  localStorage.setItem('fname', newVal)
})
watch(lname, (newVal) => {
  localStorage.setItem('lname', newVal)
})
watch(cnumber, (newVal) => {
  localStorage.setItem('cnumber', newVal)
})
onMounted(() => {
    fname.value = localStorage.getItem('fname') || ''
    lname.value = localStorage.getItem('lname') || ''
    cnumber.value = localStorage.getItem('cnumber') || ''
})
function payment(){
        if(fname.value && lname.value && cnumber.value){
        console.log("Payment function called")
        
        return router.push({name: 'thankyou'})
    }
  
    if(!fname.value|| !lname.value){
       err.value = "name is required"
    }
    if(!cnumber.value){
       err.value = "card number is required"
    }
   
      }
</script>
<template> 
  <div style="width: 600px">
           
  
      <form class="form"  @submit.prevent="payment()">
        <p style="color: red">{{ err }}</p>
        <h1>Payment details</h1> 
        
        <div class="input-l">
         <label for="fname">FIRST NAME</label>
         <input type="text"  placeholder="First name" v-model="fname" />
        </div>
        <div class="input-l">
         <label for="lname">LAST NAME</label>
         <input type="text"   placeholder="Last name" v-model="lname" />
        </div>
        <div class="input-l">
         <label for="c-type"> TYPE OF CARD </label>
        <div>
         <input type="radio" name="test" value="mastercard" checked >
         <img style="max-width: 40px" src="../assets/img/mastercard.jpg" alt="Option 1">
         
         <label>
         <input type="radio" name="test" value="visa" >
         <img style="max-width: 40px" src="../assets/img/Visa-Logo.jpg" alt="Option 2">
         </label>
         <label>
         <input type="radio" name="test" value="americane" >
         <img style="max-width: 40px" src="../assets/img/americanexpress.jpg" alt="Option 3">
         </label>
        </div>
      </div>
        <div class="input-l">
         <label for="c-number">CARD NUMBER</label>
         <input type="tel" id="c-number" placeholder="•••• •••• •••• ••••" autocomplete="c-number" v-model="cnumber"/>
        </div>

        <div class="input-l">
          <div>
              <label for="c-experity">CARD EXPERITY</label>
          </div>
          <div>
         <input type="tel" id="c-experity" placeholder="•• - ••" autocomplete="c-experity"/>
        </div>
        </div>
        <div class="input-l">
          <div>
              <label for="c-cvv">CVV</label>
          </div>
          <div>
               <input type="tel" id="c-cvv" placeholder="••••" autocomplete="off"/>
          </div>
        </div>
        

         <button  type="submit">Buy</button>

      </form>

    </div> 
</template>
<style scoped>
input{
    padding: 16px;
}
input:focus {
    outline: none;

}
.input-l {
  display:flex;
  justify-content: space-between; 
  align-items: flex-start;
  
}
.form {
  display: flex; 
  flex-direction: column; 
  gap: 20px;
}
button {
max-width: 100px;
align-self: flex-end;

}
h1 {
  font-size: 16px; 
  display: flex;
  align-self: center;
  justify-content: center;
  font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}

@media only screen and (max-width: 750px){
  .input-l {
    display:flex; 
    flex-direction: column;
    max-width: 300px;
    justify-content: center;
  }
  h1{
    align-self: flex-start;
    margin-bottom: 0;
    padding: 0;
  }

 button{
  align-self: flex-start;
  margin-inline: 300px;
 }
  
}



</style>
