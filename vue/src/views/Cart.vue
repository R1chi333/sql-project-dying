<template>
    <div>
      <h1>{{ userEmail }}</h1>
      <p>{{ purchases }}</p>
    </div>
  </template>
  
  <script>
  import { supabase } from '../lib/supabaseClient.js'
  
  export default {
    data() {
      return {
        userEmail: null, 
        purchases: null,
      }
    },
    async mounted() {
      await this.getUser() // Call getUser() when the component is mounted
    },
    methods: {
      async getUser() {
        const { data: { user } } = await supabase.auth.getUser()
        this.userEmail = user.email

        let { data: purchases, error } = await supabase
        .from('purchases')
        .select('character', 'price', 'img')
        .eq('email', user.email);
        if (error) {
            console.error(error)
        } else {
            // you would probs make the cards here 
        }     
      },
    },
  }
</script>


<!-- 01110010 01101001 01100011 01101000 01101001 01100101 00100000 01110111 01100001 01110011 00100000 01101000 01100101 01110010 01100101 -->