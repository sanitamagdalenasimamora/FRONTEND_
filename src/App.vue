<template>
  <div>
    <h2>Form Pendaftaran</h2>
    <form @submit="save($event)" id="user_form" method="POST">
        <div>
					<label>Email</label><br>
					<input type="text" name="email" id="email" placeholder="name@example" v-model="form.email" required>
				</div>
				<div>
					<label>Username</label><br>
					<input type="text" name="username" id="username" placeholder="contoh:doox" v-model="form.username" required>
				</div>
				<div>
					<label>Password</label><br>
					<input type="password" name="password" id="password" placeholder="contoh: katakunci" v-model="form.password" required>
				</div>
        <button type="submit">Daftar</button>
      </form>
      <ul>
        <li v-for="user in users" :key="user.id">
          {{ user.email }}
          {{ user.username }}
        </li>
      </ul>
     
  </div>
</template>
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
<script type="text/javascript" src="https://unpkg.com/vue@2.5.6/dist/vue.js"></script>
<script>
import axios from 'axios'
export default {
  data() {
    return {
        form: {
          email: '',
          username: '',
        },
        user: []
        }
  },
  methods: {
    // async load() {
    //   const response = await axios.get('http://localhost:3000/api/v1/user/daftar')
    //   this.user = response.data
    // },
   
    save(event) {
        console.log(event)
        var response = axios.post('http://localhost:3000/api/v1/user/daftar', this.form)
        this.user = response.data
        this.email = ''
        this.username = ''
        alert('Berhasil melakukan pendaftaran')
        let user_form = new FormData()
          user_form.append('email', this.email)
          user_form.append('username', this.username)
     }
  }
}
</script>