<template>
<div class="statues">
    <table>
      <thead>
        <tr>
          <th>Azonsító</th>
          <th>Person</th>
          <th>Height</th>
          <th>Price</th>
          <th>Műveletek</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="statue in statues" v-bind:key="statue.id">
          <td>{{ statue.id }}</td>
          <td>{{ statue.person }}</td>
          <td>{{ statue.height }}</td>
          <td>{{ statue.price }}</td>
        </tr>
      </tbody>
    </table>
    </div>
</template>
<script>
export default {
  name: 'Statues',
  components: {
  },
  data() {
    return {
        statue: {
        id: null,
        person: '',
        height: '',
        price: ''
      },
      statues: []
    }
  },
  methods: {
    async loadData () {
     let Response = await fetch('http://127.0.0.1:8000/api/statues')
     let data = await Response.json()
     this.statues = data
    },
  }, mounted() {
    this.loadData()
  }
}
</script>