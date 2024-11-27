<script setup>
import { ref, reactive, defineEmits, onMounted } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();

const props = defineProps({
  student: {
    type: Object,
    default: () => ({
      id: "",
      name: "",
      course: "",
      email: "",
      phone: "",
    }),
  },
});

// const model = reactive({
//   student: { ...props.student },
// });

const getStudentData = (studentId) => {};

function updateStudent() {
  console.log("Updating...");
}

const emit = defineEmits(["update"]);
</script>

<template>
  <div class="container mt-5">
    <div class="card">
      <div class="card-header">
        <h4>Edit Student</h4>
      </div>
      <div class="card-body">
        <div
          class="mb-3"
          hidden
        >
          <label for="">Id</label>
          <input
            type="text"
            class="form-control"
            v-model="student.id"
          />
        </div>
        <div class="mb-3">
          <label for="">Name</label>
          <input
            type="text"
            class="form-control"
            v-model.lazy="student.name"
          />
        </div>
        <div class="mb-3">
          <label for="">Course</label>
          <input
            type="text"
            class="form-control"
            v-model="student.course"
          />
        </div>
        <div class="mb-3">
          <label for="">Email</label>
          <input
            type="text"
            class="form-control"
            v-model="student.email"
          />
        </div>
        <div class="mb-3">
          <label for="">Phone</label>
          <input
            type="text"
            class="form-control"
            v-model="student.phone"
          />
        </div>
        <div class="mb3">
          <button
            type="button"
            class="btn btn-primary"
            @click="$emit('update', student)"
          >
            Update
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
