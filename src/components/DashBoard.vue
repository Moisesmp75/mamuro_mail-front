<template>
  <div class="p-4">
    <h3 class="text-2xl font-bold mb-4">Dashboard</h3>
    <div class="overflow-x-auto">
      <table class="min-w-full table-fixed">
        <thead class="">
          <tr>
            <th class="px-4 py-2">MessageId</th>
            <th class="px-4 py-2">From</th>
            <th class="px-4 py-2">To</th>
            <th class="px-4 py-2">Content</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(mail, i) in mails" :key="i" class="border-t align-top">
            <td class="px-4 py-2">{{ mail._source.message_id }}</td>
            <td class="px-4 py-2">{{ mail._source.from }}</td>
            <td class="px-4 py-2">
              <ul class="list-inside list-none">
                <li v-for="(item, i) in mail._source.to" :key="i" class="whitespace-nowrap">{{ item }}</li>
              </ul>
            </td>
            <td class="px-4 py-2" v-html="mail._source.content">
            </td>
          </tr>
        </tbody>
      </table>
      <!-- {{ this.mails }} -->
    </div>
  </div>
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
  },
  cleanEmail(email) {
    return email.replace(/[\r\t\n]/g, '').trim();
  },
  methods: {
    formatContent(content) {
      const paragraphs = content.split('\n\n'); // Dividir por párrafos
      const formattedContent = paragraphs.map(paragraph => `${paragraph}`).join('');
      return formattedContent;
    }
  }

}
</script>
<style></style>