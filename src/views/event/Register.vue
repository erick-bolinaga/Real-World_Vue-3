<template>
    <p>Register for the event here</p>
    <button @click="register">Register me</button>
</template>

<script>
export default {
    props: ["event"],
    inject: ["GStore"],
    methods: {
        register() {
            // Call to API
            // If registered then redirect to event details
            this.GStore.flashMessage = "You are successfully registered for" + this.event.title;
            setTimeout(() => {
                this.GStore.flashMessage = ""
            }, 3000);
            this.$router.push({
                name: "EventDetails",
                // params: { id: this.event.id } ... Since is a nested route and id is required by the parent route, we don't need to pass it
            });
            // this.$router.replace ... The same like push but without creating a history entry
            // this.$router.go(1)  or -1 .. move forward or backward in the history
        }
    }
}
</script>
