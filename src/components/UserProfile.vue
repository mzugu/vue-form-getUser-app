<template>
  <div v-if="picture"><img :src="picture" :class="gender" alt="user" /></div>
  <h1>{{ firstName }} {{ lastName }}</h1>
  <h3>
    {{ email }}
  </h3>
  <button @click="getUser" :class="gender">Get User</button>
</template>

<script>
export default {
  name: "UserProfile",
  data() {
    return {
      firstName: "",
      lastName: "",
      email: "",
      picture: "",
      gender: ""
    };
  },
  methods: {
    async getUser() {
      const res = await fetch("https://randomuser.me/api");
      const { results } = await res.json();
        (this.firstName = results[0].name.first),
        (this.lastName = results[0].name.last),
        (this.picture = results[0].picture.large),
        (this.email = results[0].email);
        (this.gender = results[0].gender);
    },
  },
};
</script>

<style scoped>
h1,
h3 {
  font-weight: normal;
  margin-bottom: 1rem;
}
img {
  border: 5px #333 solid;
  border-radius: 50%;
  margin-bottom: 1rem;
}
button {
  cursor: pointer;
  display: inline-block;
  color: white;
  font-size: 18px;
  background: #333;
  border: 0;
  padding: 1rem 1.5rem;
}
.female {
  border-color: pink;
  background-color: pink;
  color: #333;
}
.male {
  border-color: steelblue;
  background-color: steelblue;
}
</style>