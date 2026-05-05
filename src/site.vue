<template>
  <main class="page">
    <section class="hero">
      <h1>Bright Future Academy</h1>
      <p>Quality education for future leaders.</p>
      <button>Apply Now</button>
    </section>

    <section class="about">
      <h2>About Our School</h2>
      <p>
        Bright Future Academy provides modern learning, experienced teachers,
        and a safe environment for students to grow.
      </p>
    </section>

    <section class="form-section">
      <h2>Student Admission Form</h2>

      <form @submit.prevent="submitForm">
        <input v-model="form.name" type="text" placeholder="Student Name" required />
        <input v-model="form.email" type="email" placeholder="Parent Email" required />
        <input v-model="form.phone" type="tel" placeholder="Phone Number" required />

        <select v-model="form.classLevel" required>
          <option disabled value="">Select Class</option>
          <option>Nursery</option>
          <option>Primary</option>
          <option>Junior Secondary</option>
          <option>Senior Secondary</option>
        </select>

        <textarea v-model="form.message" placeholder="Message"></textarea>

        <button type="submit">Submit Application</button>
      </form>

      <p v-if="submitted" class="success">
        Application submitted successfully!
      </p>
    </section>
  </main>
</template>

<script setup>
import { reactive, ref } from "vue";

const submitted = ref(false);

const form = reactive({
  name: "",
  email: "",
  phone: "",
  classLevel: "",
  message: "",
});

function submitForm() {
  console.log("Form submitted:", form);

  submitted.value = true;

  form.name = "";
  form.email = "";
  form.phone = "";
  form.classLevel = "";
  form.message = "";
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f4f7fb;
  color: #1f2937;
}

.page {
  min-height: 100vh;
}

.hero {
  padding: 80px 20px;
  text-align: center;
  background: linear-gradient(135deg, #2563eb, #1e40af);
  color: white;
}

.hero h1 {
  font-size: 42px;
  margin-bottom: 10px;
}

.hero p {
  font-size: 18px;
}

button {
  border: none;
  background: #facc15;
  color: #111827;
  padding: 14px 22px;
  border-radius: 10px;
  font-weight: bold;
  cursor: pointer;
}

.about,
.form-section {
  max-width: 700px;
  margin: 40px auto;
  padding: 25px;
  background: white;
  border-radius: 18px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.08);
}

form {
  display: grid;
  gap: 14px;
}

input,
select,
textarea {
  width: 100%;
  padding: 14px;
  border: 1px solid #d1d5db;
  border-radius: 10px;
  font-size: 16px;
}

textarea {
  min-height: 120px;
}

.success {
  color: #15803d;
  font-weight: bold;
  margin-top: 15px;
}

@media (max-width: 600px) {
  .hero h1 {
    font-size: 32px;
  }

  .about,
  .form-section {
    margin: 20px;
  }
}
</style>
