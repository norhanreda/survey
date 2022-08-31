<template>
  <base-card>
  
    <h1>How was your learning exprience ? </h1>
    <form @submit.prevent="submitExperience" >
      <div class="form-control">
   <label>Your Name: </label>
    <input type="text" name="name" id="name" v-model.trim="name"    />
      </div>
       <div class="form-control">
      <label>My learning exprience was...</label>
      </div>
      <div class="form-control">
        <label>Poor </label>
        <input id="poor" name="rating" value="poor" v-model="rating" type="radio"  />
        
      </div>

      <div class="form-control">
        <label> Average</label>
        <input id="average" name="rating"  value="average" v-model="rating" type="radio"  />
        
      </div>
      

      <div class="form-control">
        <label>Great </label>
        <input id="great" name="rating" value="great" v-model="rating" type="radio"   />
       
      </div>
         <p v-if="error"  style="color:red">  {{error}}</p>
      <div class="form-control">
        <base-button type="submit" >Submit </base-button>
    </div>
    <p v-if="invalidInput">Please enter all fields </p>

    </form>
  
  </base-card>
</template>

<script>

import BaseButton from '../UI/BaseButton.vue';
export default {
  components: { BaseButton },
  data ()
  {
    return{
     name:'',
     rating:null,
     invalidInput:false,
     error:null,
     };
  },
  // emits: ['survey-submit'],
  methods:
  {
  submitExperience()
  {
      if(this.name==='' || !this.rating )
     {
       this.invalidInput=true;
       return;
     }
       
     this.invalidInput = false;
    //  this.$emit('survey-submit', {
    //     name: this.name,
    //     rating: this.rating,
    //   });
      fetch('https://survey-8b056-default-rtdb.firebaseio.com/survey.json',
      {
      method:'POST',
      headers:{
       'Content-Type':'application/json'
      },
      body: JSON.stringify({
          name:this.name,
          rating:this.rating,
      }),

      }
      
      ).then (response =>
      {
         
        if(response.ok)
        {
              console.log('done......');
        }
        else
        {
          throw new Error('Could not save data! ');
        }
      }
        

      ).catch((Error)=>
      {
        console.log(Error);
        this.error=Error.message;
      });
     this.name='';
     this.rating=null;

  },

  },
  
};
</script>

<style scoped>
.form-control
{
margin: 0.5rem 0;
}
input[type='text'] {
  display: block;
  width: 20rem;
  margin-top: 0.5rem;
}

</style>