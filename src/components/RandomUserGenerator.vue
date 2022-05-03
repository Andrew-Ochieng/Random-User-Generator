<template>
  <div>
    <img :class="gender" v-bind:src="picture" :alt="`${firstName} ${lastName}`">
    <h1>{{title}} {{firstName}} {{lastName}}</h1>
    <h3>Email: {{email}}</h3>
    <h3>Location: {{city}}, {{country}}</h3>
    <h3>Phone: {{phone}}</h3>
    <button @click="getUser()" :class="gender">Get Random User</button>
  </div>
</template>

<script>
  export default {
    name: 'RandomUserGenerator',
    data(){
      return{    
        title: 'Dr',
        firstName: 'John',
        lastName: 'Doe',
        email: 'johndoe@gmail.com',
        city: 'Tennessee',
        country: 'USA',
        gender: 'male',
        phone: '49104661',
        picture: 'https://randomuser.me/api/portraits/men/61.jpg' 
      }
    },


    methods: {
      async getUser(){
        const res = await fetch('https://randomuser.me/api')
        const { results } = await res.json()

        // console.log(results)
        // console.log(this.lastName)

        this.title = results[0].name.title,
        this.firstName = results[0].name.first,
        this.lastName = results[0].name.last,
        this.email = results[0].email,
        this.city = results[0].location.city,
        this.country = results[0].location.country,
        this.gender = results[0].gender,
        this.phone = results[0].phone,
        this.picture = results[0].picture.large
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>