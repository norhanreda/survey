<template>
  <section>
    <base-card>
      <h2>Submitted Experiences</h2>
      <div>
        <base-button @click="loadData()">Load Submitted Experiences</base-button>
      </div>
      <p v-if="isLoading">Loading data please wait.......... </p>
      <p v-else-if="!isLoading && (!results || results.length===0)">There is no Data</p>
      <ul  v-else-if="!isLoading && results &&results.length>0">
        <survey-result
          v-for="result in results"
          :key="result.id"
          :name="result.name"
          :rating="result.rating"
        ></survey-result>
      </ul>
    </base-card>
  </section>
</template>

<script>


import SurveyResult from './SurveyResult.vue';

export default {
  data()
  {
    return {
      isLoading:null,
      results:[],
    };
  },

  components: {
    SurveyResult,
  },
  methods:
  {
   
    loadData()
    {
      this.isLoading=true;
      fetch('https://survey-8b056-default-rtdb.firebaseio.com/survey.json')
      .then((response)=>{
            if(response.ok)
             {
                return response.json();
             }

      }).then((data)=>{
        this.isLoading=false;
           console.log(data);
          const res=[];
          for(const id in data)
          {
              res.push({id:id,name:data[id].name,rating:data[id].rating});
          }
          this.results=res;
      },
     
      );

    },
  },
 mounted()
 {
  this.loadData();
 }

};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>