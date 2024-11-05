<template>
  <div class="container">
    <div v-for="(message) in messages" :key="message" class="contentChatUser" :style="{alignItems:message.aligne}">
        <p>{{message.name}}</p>
        <p class="pmessage" :style="{backgroundColor:message.color}">{{message.text}}</p>
    </div>

  </div>    
</template>
<script>
export default {
    name: 'Chat',
    props:{
        messages: Array,

    },
};
</script>

<style scoped>
.container {
    
    height: 585px;
    width: 25%;
    margin: 5px;
    border: 1px solid white;
    background-color: rgb(208, 205, 205);
    overflow-y: auto;
    padding-top: 15px;
}
.contentChatUser {
    display: flex;
    flex-direction: column;
}
.pmessage{
    width: max-content;
    padding: 10px;
    border-radius: 15px;
   
}
p{
    margin: 2px 0 2px 0;
    padding-left: 2px;
}
</style>