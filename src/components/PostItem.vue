<template>
<div class="post">
            <div><strong>Название: </strong> {{ post.title }}</div>
            <div><strong>Описание: </strong> {{ post.body }}</div>
    </div>
</template>


<script>
export default {
    components: {PostItem},
    props: {
        post: {
            type: Object,
            requred: true,
        }
    }
}

</script>

<style scoped>

</style>

