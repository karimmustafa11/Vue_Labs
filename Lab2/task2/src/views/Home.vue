<template>
  <div style="padding: 1rem;">
    <h2>Student Management</h2>

    <!-- Form -->
    <div style="margin-bottom: 1rem;">
      <input v-model="form.id" placeholder="ID" :disabled="isEditing" />
      <input v-model="form.name" placeholder="Name" />
      <input v-model="form.city" placeholder="City" />
      <button @click="isEditing ? updateStudent() : addStudent()">
        {{ isEditing ? 'Update' : 'Add' }}
      </button>
      <button v-if="isEditing" @click="resetForm()">Cancel</button>
    </div>

    <!-- Table -->
    <table border="1" style="width: 100%; text-align: center; border-collapse: collapse;">
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>City</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(student, index) in students" :key="student.id">
          <td>{{ student.id }}</td>
          <td>{{ student.name }}</td>
          <td>{{ student.city }}</td>
          <td>
            <button @click="editStudent(index)">Edit</button>
            <button @click="deleteStudent(index)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      students: [
        { id: 100, name: 'Mario', city: 'Assiut' },
        { id: 200, name: 'Abd el rahman', city: 'Cairo' },
        { id: 300, name: 'Islam', city: 'Alexandria' },
        { id: 400, name: 'Gehad', city: 'Minia' },
        { id: 500, name: 'Nourhan', city: 'Aswan' },
      ],
      form: {
        id: '',
        name: '',
        city: ''
      },
      isEditing: false,
      editingIndex: null
    };
  },
  methods: {
    addStudent() {
      if (!this.form.id || !this.form.name || !this.form.city) return alert('Please fill all fields');
      this.students.push({ ...this.form });
      this.resetForm();
    },
    editStudent(index) {
      const student = this.students[index];
      this.form = { ...student };
      this.isEditing = true;
      this.editingIndex = index;
    },
    updateStudent() {
      if (this.editingIndex !== null) {
        this.students[this.editingIndex] = { ...this.form };
        this.resetForm();
      }
    },
    deleteStudent(index) {
      if (confirm('Are you sure you want to delete this student?')) {
        this.students.splice(index, 1);
        if (index === this.editingIndex) this.resetForm();
      }
    },
    resetForm() {
      this.form = { id: '', name: '', city: '' };
      this.isEditing = false;
      this.editingIndex = null;
    }
  }
};
</script>
