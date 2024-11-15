<script setup>
import { reactive, defineEmits, onMounted } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();

const model = reactive({
  student: {
    name: "",
    course: "",
    email: "",
    phone: "",
  },
});

onMounted(() => {
  console.log(route.params.id);
});

const getStudentData = (studentId) => {};
</script>

<template>
  <div class="container mt-5">
    <div class="card">
      <div class="card-header">
        <h4>Edit Student</h4>
      </div>
      <div class="card-body">
        <div class="mb-3">
          <label for="">Name</label>
          <input
            type="text"
            class="form-control"
            v-model="model.student.name"
          />
        </div>
        <div class="mb-3">
          <label for="">Course</label>
          <input
            type="text"
            class="form-control"
            v-model="model.student.course"
          />
        </div>
        <div class="mb-3">
          <label for="">Email</label>
          <input
            type="text"
            class="form-control"
            v-model="model.student.email"
          />
        </div>
        <div class="mb-3">
          <label for="">Phone</label>
          <input
            type="text"
            class="form-control"
            v-model="model.student.phone"
          />
        </div>
        <div class="mb3">
          <button
            type="button"
            class="btn btn-primary"
            @click="saveStudent"
          >
            Save
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
