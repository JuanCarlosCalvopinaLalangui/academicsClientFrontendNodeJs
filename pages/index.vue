<template>
  <div>
    <!-- easy components usage, already shipped with bootstrap css-->
    <b-container>
      <!-- try to remove :fields=”fields” to see the magic -->
      <b-table striped over :items="students" :fields="fields" />
    </b-container>
    <nuxt-link to="/createStudent">Create a New Student</nuxt-link>
    <nuxt-link to="/createCourse">Create a New Course</nuxt-link>
  </div>
</template>

<script>
export default {
  data () {
    return {
      fields: ['username', 'name', 'email'],
      students: []
    }
  },
  created () {
    this.$axios.$get('/api/students')
      .then((students) => {
        this.students = students
      })
  }
}
</script>
