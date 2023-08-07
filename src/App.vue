<template>
    <div class="app">
        <post-form
        @create="createPost"
        /> 
        <post-list 
        :posts="posts"
        />
    </div>
   
</template>   


<script>
import PostForm from '@/components/PostForm';
import PostList from '@/components/PostList';

export default {
    components: {
        PostList, PostForm
    },
    data() {
        return {
            posts: [
                {id:1, title: 'JavaScript', body: 'Описание Поста 1'},
                {id:2, title: 'JavaScript', body: 'Описание Поста 2'},
                {id:3, title: 'JavaScript', body: 'Описание Поста 3'},  
            ],
        }
    },
    methods: {
        createPost(post) {
            this.posts.push(post)
        },
    }

}
</script>

<style>
*{
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
}
.app {
    padding: 20px;
}


</style>