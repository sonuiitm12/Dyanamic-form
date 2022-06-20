<template>
  <div id="app" class="container">
    <form>
      <h1>Create dynamic form generator</h1>
      <div class="work-experiences">

        <div class="form-row" v-for="(experience, index) in workExperiences" :key="index">
          <div class="form-group col-md-6">
            <label>Question</label>
            <input v-model="experience.Question" :name="`workExperiences[${index}][Question]`" type="text" class="form-control" placeholder="Question">
          </div>
          <div class="form-group col-md-6">
            <label>Answer</label>
            <input v-model="experience.Answer" :name="`workExperiences[${index}][Answer]`" type="text" class="form-control" placeholder="Answer">
          </div>
        </div>
      </div>

      <div class="form-group">
        <button @click="addExperience" type="button" class="btn btn-secondary">Add Section</button>
      </div>
      
      <hr>

      <div class="form-group">
        <button @click="submit" type="button" class="btn btn-primary">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>

export default {
  name: "App",
  
  data: () => ({
    workExperiences: [
      {
        Question: "Add question here",
       Answer : "Add Answer here"
      },
      {
        Question: "Add question here",
        Answer: "Add Answer here"
      }
    ]
  }),

  methods: {
    addExperience () {
      this.workExperiences.push({
        Question: 'Add question here ',
        Answer: 'Add Answer here'
      })
    },

    submit () {
      const data = {
        workExperiences: this.workExperiences
      }
      alert(JSON.stringify(data, null, 2))
    }
  }
};
</script>

<style>
.work-experiences > div {
  margin: 20px 0;
  padding-bottom: 10px;
}
.work-experiences > div:not(:last-child) {
  border-bottom: 1px solid rgb(206, 212, 218);
}
</style>
