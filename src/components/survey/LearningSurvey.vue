<template>
  <base-card>
  
    <h1>How was your learning exprience ? </h1>
    <form >
      <div class="form-control">
   <label>Your Name: </label>
    <input type="text" name="name" id="name" v-model="name"    />
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

      <div class="form-control">
        <base-button type="submit" >Submit </base-button>
    </div>

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
     rating:'',
     invalidInput:false,
     };
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