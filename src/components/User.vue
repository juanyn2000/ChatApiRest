<template>
  <div class="user">
    <img :src="user.image" alt="Foto-perfil" />
    <h3 class="nameUser">{{ user.name }}</h3>
    <input v-model="user.colorMessage" type="color" />
    <textarea v-model="user.message" cols="30" rows="10"></textarea>
    <button @click="send">Enviar</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "User",
  props: {
    color: String,
    position: String,
  },
  data() {
    return {
      user: {
        name: String,
        image: String,
        message: "",
        colorMessage: this.color,
      },
      historyMessage: {},
    };
  },
  async mounted() {
    const response = await axios.get("https://randomuser.me/api/");
    this.user.name =
      response.data.results[0].name.first +
      " " +
      response.data.results[0].name.last;
    this.user.image = response.data.results[0].picture.large;
  },
  methods: {
    send() {
      if (this.user.message === "") {
        return;
      }
      this.historyMessage = {
        text: this.user.message,
        name: this.user.name,
        color: this.user.colorMessage,
        aligne: this.position,
      };
      this.$emit("send", this.historyMessage);
      this.user.message = "";
    },
  },
};
</script>

<style scoped>
.user {
  width: max-content;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
input {
  width: 100%;
}
</style>
