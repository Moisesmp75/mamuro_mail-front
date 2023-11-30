<template>
  <h1 class="inset-0 text-5xl font-medium bg-violet-900 text-white underline decoration-double">Mamuro Mail</h1>
  <Input v-model="this.query" />
  <Button textButton="Aceptar" :onClick="search_data" />
  <DashBoard :data="this.mails" />
</template>
<script>

import { MailServices } from '../services/mail-service';

import Input  from '../components/Input.vue'
import Button from "../components/Button.vue"
import DashBoard from '../components/DashBoard.vue';


export default {
    
    components: { Button, Input, DashBoard },
    created() {
      this.mailService = new MailServices()
    },
    data() {
      return {
        query: "",
        pages: 10,
        mails: []
      }
    },
    methods: {
      async search_data() {
        const request = { query: this.query, pages: this.pages }
        const { resource } = await this.mailService.search_data(request)
        const { hits } = resource
        const { hits: mails } = hits
        this.setMails(mails)
      },
      setMails(newMails) {
        console.log(this.mails)
        this.mails = [...newMails]
        console.log(this.mails)
      },
      created() {
        this.mails = [""]
      }
    }
}
</script>
<style>
  
</style>