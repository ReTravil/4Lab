<template>
    <Page>
        <ActionBar title="Calculator"/>
        <todo-item></todo-item>
    </Page>
</template>

<script >
import TodoItem from './TodoItem.vue';
  export default {
    components: { TodoItem }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }
</style>
