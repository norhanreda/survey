<template>
  <learning-survey @survey-submit="storeSurvey"> </learning-survey>
 <user-experiences :results="savedSurveyResults"> </user-experiences>
</template>

<script>
import LearningSurvey from './components/survey/LearningSurvey.vue';
import UserExperiences  from './components/survey/UserExperiences.vue';


export default {
  components: {
    LearningSurvey,
    UserExperiences,
  },
  data() {
    
    return {
      savedSurveyResults: [],
    };
  },
  methods:
  {
  storeSurvey(data)
  {
   const survey={
       name:data.name,
       rating:data.rating,
       id :new Date().toISOString(),
   };
   this.savedSurveyResults.push(survey);
   console.log(survey);
  },
  },

  
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>