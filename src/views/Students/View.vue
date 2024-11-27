<script setup>
import { ref, onMounted, reactive } from "vue";
import Create from "./Create.vue";
import Edit from "./Edit.vue";

const students = ref([
  {
    id: 1,
    name: "student 1",
    course: "course 1",
    email: "email 1",
    phone: "phone 1",
    created_at: "2024-10-17",
    updated_at: "2024-10-18",
  },
  {
    id: 2,
    name: "student 2",
    course: "course 2",
    email: "email 2",
    phone: "phone 2",
    created_at: "2024-10-17",
    updated_at: "2024-10-18",
  },
  {
    id: 3,
    name: "student 3",
    course: "course 3",
    email: "email 3",
    phone: "phone 3",
    created_at: "2024-10-17",
    updated_at: "2024-10-18",
  },
]);

onMounted(() => {
  console.log("Oki");
});

function getStudents() {
  return students;
}

function addStudent(student) {
  student.id = students.value.length + 1;
  const formattedDate = new Date().toISOString().split("T")[0];
  student.created_at = formattedDate;
  student.updated_at = formattedDate;
  students.value.push(student);
}

function deleteStudent(studentId) {
  students.value = students.value.filter((student) => student.id !== studentId);
}

function editStudent(student) {
  model.student = student;
}

const model = reactive({
  student: {
    name: "",
    course: "",
    email: "",
    phone: "",
  },
});

function updateStudent(student) {
  const index = students.value.findIndex((s) => s.id === student.id);
  if (index !== -1) {
    student.updated_at = new Date().toISOString().split("T")[0];
    students.value[index] = { ...student };
  }

  model.student = {
    name: "",
    course: "",
    email: "",
    phone: "",
  };
}
</script>

<template>
  <Create @add-student="addStudent" />
  <div class="container">
    <div class="card">
      <div class="card-header">
        <h4>
          Students
          <RouterLink
            to="/students/create"
            class="btn btn-primary float-end"
            >Add Student</RouterLink
          >
        </h4>
      </div>
      <div class="card-body">
        <table class="table table-bordered">
          <thead>
            <tr>
              <th>Id</th>
              <th>Name</th>
              <th>Course</th>
              <th>Email</th>
              <th>Phone</th>
              <th>Created At</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="(student, index) in students"
              :key="student.id"
            >
              <td>{{ student.id }}</td>
              <td>{{ student.name }}</td>
              <td>{{ student.course }}</td>
              <td>{{ student.email }}</td>
              <td>{{ student.phone }}</td>
              <td>{{ student.created_at }}</td>
              <td>
                <button
                  class="btn btn-success"
                  @click="editStudent(student)"
                >
                  Edit
                </button>
                <button
                  class="btn btn-danger"
                  @click="deleteStudent(student.id)"
                >
                  Delete
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
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
            @click="updateStudent(model.student)"
          >
            Update
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
