<template>
    <li>
        <input type="checkbox" :checked="checked" /> {{idol.name}}
    </li>
</template>

<script>
    export default {
        name : "CheckboxItem",
        props : ["name", "checked"],
        created() {
            this.checked = true;
        }
    }
</script>

<style scoped>

</style>