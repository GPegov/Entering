<template>
    <div class="app">
        <my-dialog :show="true">
            <post-form
        @create="createPost"
        /> 
        </my-dialog>
        
        <post-list 
        :posts="posts"
        @remove="removePost"
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
        removePost(post){
            this.posts = this.posts.filter(p => p.id !== post.id)
        }
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