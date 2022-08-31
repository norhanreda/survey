<template>
  <section>
    <base-card>
      <h2>Submitted Experiences</h2>
      <div>
        <base-button @click="loadData()">Load Submitted Experiences</base-button>
      </div>
      <ul >
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
      load:false,
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
      fetch('https://survey-8b056-default-rtdb.firebaseio.com/survey.json')
      .then((response)=>{
            if(response.ok)
             {
                return response.json();
             }

      }).then((data)=>{

           console.log(data);
          const res=[];
          for(const id in data)
          {
              res.push({id:id,name:data[id].name,rating:data[id].rating});
          }
          this.results=res;
      });

    },
  },

};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>