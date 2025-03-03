<!-- our html template -->
<template>
  <div class="container">
    <h1>Student Information</h1>
    <div class="getInfoField">
      <input v-model="newStudent.fullName" placeholder="Name" />
      <input v-model="newStudent.phoneNumber" type="number" placeholder="phone number" />
      <input v-model="newStudent.description" placeholder="description" />
      <input v-model="newStudent.country" placeholder="country" />
      <input v-model="newStudent.address" placeholder="address" />
      <button @click="addStudent">Add Student</button>
    </div>
    <div class="studentGrid">
      <div v-for="(student, index) in students" :key="index" class="student-card">
        <img v-bind:src="student.profilePicture" v-bind:alt="student.name" class="student-photo" />
        <h2 class="student-name">{{ student.fullName }}</h2>
        <p class="student-age"><b>Description:</b> {{ student.description }}</p>
        <p class="student-age"><b>Phone: </b>{{ student.phoneNumber }}</p>
        <p class="student-age"><b>Country:</b> {{ student.country }}</p>
        <p class="student-age"><b>Address:</b> {{ student.address }}</p>
        <button @click="deleteStudent(index)">Delete</button>
      </div>
    </div>
  </div>
</template>

<!-- our script -->
<script>
export default {
  data() {
    return {
      students: [
        {
          "fullName": "Simon Peter",
          "description": "A passionate Vue.js developer with expertise in creating dynamic user interfaces and single-page applications. Simon enjoys collaborating with teams to build scalable web applications that enhance user experience.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8901",
          "country": "United States",
          "address": "123 Main St, Springfield, IL"
        },
        {
          "fullName": "Alice Johnson",
          "description": "A skilled front-end developer specializing in Vue.js and React. Alice has a knack for designing beautiful and responsive web applications that meet user needs.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8902",
          "country": "Canada",
          "address": "456 Maple Ave, Toronto, ON"
        },
        {
          "fullName": "Michael Smith",
          "description": "An enthusiastic software engineer with a focus on Vue.js and back-end integration. Michael loves tackling complex problems and delivering efficient solutions.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8903",
          "country": "Australia",
          "address": "789 Pine St, Sydney, NSW"
        },
        {
          "fullName": "Jessica Brown",
          "description": "A creative web developer with a strong background in Vue.js and user experience design. Jessica is dedicated to crafting intuitive interfaces that engage users.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8904",
          "country": "United Kingdom",
          "address": "101 High St, London"
        },
        {
          "fullName": "David Wilson",
          "description": "A motivated full-stack developer with experience in Vue.js and Node.js. David enjoys building robust applications that are both functional and visually appealing.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8905",
          "country": "Germany",
          "address": "202 Elm St, Berlin"
        },
        {
          "fullName": "Emily Davis",
          "description": "A detail-oriented software developer with expertise in Vue.js and agile methodologies. Emily is passionate about delivering high-quality code and improving development processes.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8906",
          "country": "France",
          "address": "303 Oak St, Paris"
        },
        {
          "fullName": "Chris Martin",
          "description": "An innovative web developer specializing in Vue.js and responsive design. Chris enjoys creating seamless user experiences and is always eager to learn new technologies.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8907",
          "country": "Italy",
          "address": "404 Birch St, Rome"
        },
        {
          "fullName": "Sophia Lee",
          "description": "A dynamic software engineer with a focus on Vue.js and cloud technologies. Sophia is passionate about building scalable applications that enhance productivity.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8908",
          "country": "Spain",
          "address": "505 Cedar St, Madrid"
        },
        {
          "fullName": "James Taylor",
          "description": "A resourceful developer with experience in Vue.js and mobile app development. James loves creating applications that bridge the gap between users and technology.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8909",
          "country": "Netherlands",
          "address": "606 Walnut St, Amsterdam"
        },
        {
          "fullName": "Olivia White",
          "description": "A passionate front-end developer with expertise in Vue.js and design systems. Olivia focuses on building accessible and user-friendly interfaces.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8910",
          "country": "Sweden",
          "address": "707 Cherry St, Stockholm"
        }
      ],
      newStudent: { fullName: '', description: '', phoneNumber: '', country: "", address: "" }
    };
  },
  methods: {
    addStudent() {
      if (this.newStudent.fullName && this.newStudent.description && this.newStudent.country && this.newStudent.address && this.newStudent.phoneNumber) {
        this.students.push({ ...this.newStudent, profilePicture: "https://placehold.co/600x400"});
        this.newStudent = { fullName: '', description: '', phoneNumber: '', country: "", address: "" };
      }
    },
    deleteStudent(index) {
      this.students.splice(index, 1);
    }
  }
};
</script>

<!-- our styles -->
<style>
.container {
  max-width: 800px;

  margin: auto;
  text-align: center;
}


.studentGrid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
  justify-items: center;
  align-items: center;
}

.student-photo {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 10px;
}


.student-name {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 5px;
   color: rgb(66, 61, 61);
}

.student-age {
  font-size: 14px;
  color: gray;
}

.student-card:hover {
  transform: scale(1.05);
}

.student-card {
  background: #efefef;
  padding: 15px;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  text-align: center;
  transition: transform 0.3s ease-in-out;
}

* {
  background-color: #efefef;
}

h1 {
  margin-bottom: 6rem;
  color: rgb(66, 61, 61);
}

input {
  margin: 2px;
  padding: 6px;
  border-radius: 8px;
  border: 1px solid rgb(182, 182, 182);
}

.getInfoField {
  display: flex;
  margin-bottom: 5rem;
}

@media screen and (min-width: 375px) {
  .getInfoField {
    display: block;
    text-align: center;
  }
}

button {
  margin: 5px;
  padding: 6px;
  background-color: rgb(66, 61, 61);
  cursor: pointer;
  color: white;
  border-radius: 8px;
}
button:hover{
  background-color: black;
  scale: 1.1;
}
</style>
