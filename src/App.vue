<template>
<v-app>
  <v-main>
    <v-app-bar color="#18FFFF"> Bem vindo, {{ firstName }}!
      <delete-all-posts-button @delete-all="clearTimeline($event)"/>
    </v-app-bar>
    <div class="messages-container">
      <div v-for="(message, index) in messages" :key="index">
        <message-card @edit-post="editPost" @remove-post="removePost" :messageProp="message"/>
      </div>
    </div>
    <bottom-bar @send-message="addMessage($event)" />   
  </v-main>  
</v-app>
</template>

<script>

import MessageCard from './components/MessageCard.vue'
import BottomBar from './components/BottomBar.vue'
import DeleteAllPostsButton from './components/DeleteAllPostsButton.vue'

export default {
  components: {
    MessageCard,
    BottomBar,
    DeleteAllPostsButton
  },
  data() {
    return {
      nome: "Vítor Bárrios",
      messages: []
      
    }
  },
  computed: {
    firstName() {
      console.log('FirstName')
      return this.nome.split(' ')[0]
    }
  },
  methods: {

    addMessage(event) {
      console.log(event)      
      this.messages.push(event)
    },

    editPost() {
        
    },

    removePost(post) {   
      console.log(post)
      const toRemove = this.messages.indexOf(post)
      this.messages.splice(toRemove, 1)
    },

    clearTimeline(event) {
      console.log(event)
      this.messages = []
    }
    
  }
}
</script>

<style>
</style>