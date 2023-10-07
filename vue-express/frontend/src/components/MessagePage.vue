<script>
import io from "socket.io-client";
import MessageComponent from "./MessageComponent.vue";

export default {
    props: {
        userName: {
            type: String,
            required: true,
        },
    },
    components: {
        MessageComponent,
    },
    data() {
        return {
            message: "",
            messages: [],
        };
    },
    methods: {
        sendMessage() {
            console.log("sendMessage: " + this.userName);
            this.socket.emit("message", {
                userName: this.userName,
                text: this.message,
                timestamp: Date.now(),
            });
            this.message = "";
        },
    },
    mounted() {
        this.socket = io("http://localhost:3000");
        this.socket.on("message", (msg) => {
            this.messages.push({
                timestamp: msg.timestamp,
                text: msg.text,
                userName: msg.userName,
            });
        });
    },
};
</script>

<template>
    <div v-for="msg in messages" :key="msg.id">
        <MessageComponent
            class="message"
            :browserUsername="userName"
            :messageUsername="msg.userName"
            :message="msg.text"
            :timestamp="msg.timestamp"
        />
    </div>
    <input class="input" v-model="message" @keyup.enter="sendMessage" />
</template>

<style>
.input {
    width: 90%;
    margin: 10px 0;
    padding: 5px;
}
.message {
    margin: 10px 0;
    padding: 5px;
    border: 1px solid black;
    background-color: lightblue;
}
.owner {
    background-color: grey;
}
</style>
