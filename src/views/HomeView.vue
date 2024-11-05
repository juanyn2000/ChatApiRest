<script >
import User from '../components/User.vue'
import Chat from '../components/Chat.vue'
export default {
  components: {
    User,
    Chat
  },
  data(){
    return {
    users: []
    }
  },
  methods: {
    sendSave(user){
      this.users.push(user);
    }
  }
}
</script>

<template>
  <main class="main">
    <User color="#ff0000" @send="sendSave" position="flex-start" />
    <Chat :messages="users"/>
    <User color="#0000ff" @send="sendSave" position="end"/>
  </main>
</template>
<style>
.main{
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f1f1f1;
}
</style>