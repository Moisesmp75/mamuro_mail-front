<template>
  <h1 class="inset-0 text-5xl font-medium bg-violet-900 text-white underline decoration-double pt-5 pb-5 pl-3 pr-3">Mamuro Mail</h1>
  <div class=" pt-5 pb-5 pl-10 pr-10">
    <div class="flex">
      <Input v-model="this.query" />
      <Button textButton="Aceptar" :onClick="search_data" />
    </div>
    <DashBoard :data="this.mails" />
  </div>
</template>
<script>

import { MailServices } from '../services/mail-service';

import Input  from '../components/Input.vue'
import Button from "../components/Button.vue"
import DashBoard from '../components/DashBoard.vue';

import data from '../../data.json'

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
        const { resource } = data
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
      },
      cleanEmail(email) {
      return email.replace(/[\r\t\n]/g, '').trim();
      }
    }
}
</script>
<style>
  
</style>