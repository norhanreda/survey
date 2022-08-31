<template>

<li>
  <span :class="highlight"> {{name }}</span> rated the learning experience
  <span :class="ratingClass"> {{rating}} </span>
</li>
  
</template>

<script>
export default {
  props:['name','rating'],
 computed:{
  ratingClass()
  {
    return 'highlight rating--' + this.rating;
  },
  },
 
};
</script>

<style scoped>
li {
  margin: 1rem 0;
  border: 1px solid #ccc;
  padding: 1rem;
}

h3,
p {
  font-size: 1rem;
  margin: 0.5rem 0;
}

.highlight {
  font-weight: bold;
}

.rating--poor {
  color: #e8ef0a;
}

.rating--average {
  color: #9408e5;
}

.rating--great {
  color: #f804af;
}
</style>