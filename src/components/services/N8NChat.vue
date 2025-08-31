<template>
  <div id="n8n-chat"></div>
</template>

<script>
import { onMounted } from "vue";
import "@n8n/chat/style.css";
import { createChat } from "@n8n/chat";

export default {
  name: "N8NChat",
  props: {
    item: Object,
  },
  setup(props) {
    onMounted(() => {
      createChat({
        webhookUrl: props.item?.url,
        target: "#n8n-chat",
        mode: "window",
        showWelcomeScreen: false,
        defaultLanguage: "en",
        initialMessages: ["Hi there! 👋"],
        i18n: {
          en: {
            title: "Hi there! 👋",
            subtitle: "",
            footer: "",
            getStarted: "New Conversation",
            inputPlaceholder: "Type your question..",
          },
        },
        enableStreaming: false,
      });
    });
  },
};
</script>

<style>
:root {
  --chat--header-height: auto;
}
.chat-header {
  display: none !important;
}
.n8n-chat {
  bottom: 50px;
}
.chat-body {
  background-color: var(--card-background) !important;
  color: var(--text) !important;
}
.chat-message-from-bot {
  background-color: var(--background) !important;
  color: var(--text) !important;
}
.chat-window {
  border: 0px solid var(--background) !important;
  background-color: var(--background) !important;
  box-shadow: var(--card-shadow) 0px 2px 15px 0px !important;
}
.chat-input {
  background-color: var(--card-background) !important;
  color: var(--text) !important;
}
.chat-inputs textarea {
  background-color: var(--background) !important;
  color: var(--text) !important;
}
.chat-inputs textarea::placeholder {
  color: var(--text) !important;
}
.chat-footer {
  border: 1px solid var(--card-background) !important;
  background-color: var(--card-background) !important;
  color: var(--text) !important;
}
.chat-input-send-button {
  background-color: var(--card-background) !important;
  color: var(--text) !important;
}
.chat-layout {
  background-color: var(--background) !important;
}
.chat-window-toggle {
  background-color: var(--card-background) !important;
  color: var(--text) !important;
  box-shadow: var(--card-shadow) 0px 2px 15px 0px !important;
}
</style>
