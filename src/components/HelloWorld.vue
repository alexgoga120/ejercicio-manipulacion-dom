<template>
  <div class="container">
    <div class="columns is-centered">
      <div class="field mr-6">
        <div class="control">
          <label class="label">Nombre</label>
          <input v-model="title" class="input" type="text" placeholder="Nombre">
        </div>
        <div class="control">
          <label class="label">Tiempo</label>
          <input v-model="time" class="input" type="number" placeholder="Descripción">
        </div>
        <div class="control">
          <label class="label">Descripción</label>
          <textarea v-model="description" class="textarea" placeholder="Tiempo"></textarea>
        </div>
        <button @click="addTask" class="button is-link mt-4 is-pulled-left">
          <fa icon="plus"/>
          Añadir
        </button>
      </div>
      <div class="table-container">
        <table class="table is-striped ">
          <thead>
          <tr>
            <th>Nombre</th>
            <th>Descripción</th>
            <th>Tiempo</th>
            <th>Opciones</th>
          </tr>
          </thead>
          <tbody v-if="courses">
          <tr v-for="(course, index) in courses" :key="course">
            <td>{{ course.title }}</td>
            <td>{{ course.description }}</td>
            <td class="has-text-centered">{{ course.time }} hrs</td>
            <td class="has-text-centered">
              <button @click="removeCourse(index)" class="button is-danger is-small">
                <fa icon="ban"/>
              </button>
            </td>
          </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      courses: [],
      title: null,
      description: null,
      time: null
    }
  },
  computed: {
    totalTime() {
      let total = 0;

      for (let course of this.courses) {
        total = total + parseInt(course.time);
      }

      return total;
    }
  },

  methods: {
    addTask(){
      if (this.title && this.description && this.time) {
        this.courses.push({ title: this.title, time: this.time, description: this.description });
        localStorage.setItem("courses", JSON.stringify(this.courses));
      }

      this.title = null;
      this.time = null;
      this.description = null;
    },
    removeCourse(i) {
      this.courses.splice(i, 1);
      localStorage.setItem("courses", JSON.stringify(this.courses));
    }
  }
}
</script>


<style>


</style>
