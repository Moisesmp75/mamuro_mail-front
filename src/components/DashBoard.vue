<template>
  <h3>DashBoard</h3>
  <table>
    <thead>
      <tr>
        <th>MessageId</th>
        <th>From</th>
        <th>To</th>
        <th>Content</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(mail, i) in this.mails" >
        <td>{{ mail._source.message_id}}</td>
        <td>{{ mail._source.from }}</td>
        <td>{{ mail._source.to }}</td>
        <td>{{ mail._source.content }}</td>
      </tr>
    </tbody>
  </table>
  <!-- {{ this.mails }} -->
</template>
<script>
export default {
  props: {
    data: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      mails: []
    }
  },
  created() {
    this.mails = this.data
  },
  updated() {
    this.mails = this.data
  }
}
</script>
<style>
  
</style>