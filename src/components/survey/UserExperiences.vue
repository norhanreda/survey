<template>
  <section>
    <base-card>
      <h2>Submitted Experiences</h2>
      <div>
        <base-button @click="toggleLoad()">Load Submitted Experiences</base-button>
      </div>
      <ul v-if="load">
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
    };
  },
  props: ['results'],
  components: {
    SurveyResult,
  },
  methods:
  {
   toggleLoad()
   {
     this.load=!this.load;
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