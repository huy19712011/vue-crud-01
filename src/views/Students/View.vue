<script setup>
import { ref, onMounted } from "vue";
import Create from "./Create.vue";

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
  students.value.push(student);
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
                <RouterLink
                  class="btn btn-success"
                  :to="{ path: '/students/' + student.id + '/edit' }"
                >
                  Edit
                </RouterLink>
                <RouterLink
                  class="btn btn-danger"
                  to="/"
                >
                  Delete
                </RouterLink>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>
