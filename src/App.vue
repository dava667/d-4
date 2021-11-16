<template>
<transition name="modal">
<div class="wrapper">
<div class="wrapper-content">
<section>

<div class="container">
  
<button class="btn btnPrimary" @click="modalFirst = !modalFirst">Show first modal</button>

  <modals title="First modal" 
  v-show="modalFirst" 
  @close="modalFirst = false">
  <div slot="body">
<p>see how my work works</p>
<button class="btn btnPrimary" @click="modalFirst = !modalFirst">Well done</button>
</div>
  </modals>

  <button class="btn btnPrimary" @click="modalSecond.show = !modalSecond.show">Show second modal</button>

  <modals 
  title="Modal with form" 
  v-show="modalSecond.show" 
  @close="modalSecond.show = false">
  <div slot="body">
<form @submit.prevent="submitSecondForm">
  <label>Name:</label>
  <input type="text" required v-model="modalSecond.name">
  <label>Email:</label>
  <input type="text" required v-model="modalSecond.email">
<button class="btn btnPrimary" >Submit</button>
</form>
</div>
  </modals>
<button class="btn btnPrimary" @click="modalValidate = !modalValidate">Show second modal + validate</button>
<modalValidate v-show="modalValidate" @close="modalValidate=false">
    
    

</modalValidate>
</div>
</section>

</div>
</div>
</transition>
</template>

<script>
import modals from'@/components/UI/Modal.vue'
import modalValidate from'@/components/ModalValidate.vue'
export default{
components:{
  modals , modalValidate
},
data(){
  return{
   modalFirst:false,
   modalSecond:{
     show:false,
     name:'',
     email:''
   },
   modalValidate:false
  }
},
methods:{
  submitSecondForm(){
    console.log({
      name: this.modalSecond.name ,
      email: this.modalSecond.email
    })
    this.modalSecond.name =''
    this.modalSecond.email=''
    this.modalSecond.show=false
  }
}
}
</script>
