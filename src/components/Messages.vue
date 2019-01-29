<template lang="html">
  <div>
    <h1>Messages</h1>
    <div v-for="message in messageList" class="container">
      <h3>{{message.subject}}</h3>
      <p>{{message.body}}</p>
      Labels:
      <div v-for="label in message.labels">
        {{label}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Messages',
  props: {
    messages: {
      type: Array
    }
  },
  data () {
    return {
      messageList: this.messages
    }
  }
}
</script>
