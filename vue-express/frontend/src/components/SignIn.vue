<template>
    <div id="app">
        <h1>Sign In</h1>
        <div>
            <label for="name">Username: </label>
            <input
                v-model="userName"
                type="text"
                placeholder="Enter Username"
                @keyup.enter="setName"
            />
        </div>
    </div>
</template>

<script>
export default {
    name: "SignIn",
    data() {
        return {
            userName: "",
        };
    },
    methods: {
        setName() {
            console.log("New username:", this.userName);
            this.$emit("inputChange", this.userName);
        },
    },
};
</script>
