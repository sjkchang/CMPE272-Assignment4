<script>
export default {
    name: "MessageComponent",
    props: {
        browserUsername: {
            type: String,
            required: true,
        },
        messageUsername: {
            type: String,
            required: true,
        },
        message: {
            type: String,
            required: true,
        },
        timestamp: {
            type: Number,
            required: true,
        },
    },
    data() {
        return {
            owner: false,
        };
    },
    mounted() {
        if (this.browserUsername === this.messageUsername) {
            this.owner = true;
        }
    },
};
</script>

<template>
    <div class="message" v-bind:class="owner ? 'owner' : ''">
        {{ messageUsername }} - {{ message }} - {{ timestamp }}
    </div>
</template>
