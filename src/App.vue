<template>
    <div class="app">
        <h1>Страница с постами</h1>
        <my-button
        @click="fetchPosts"
        >
        Получить посты
        </my-button>
        <input type="text" v-model.trim='modificatorValue'>
        <my-button 
        @click="showDialog"
        style="margin: 15px 0;"   
        >
        Создать пост
        </my-button>
        <my-dialog v-model:show="dialogVisible">
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
import axios from 'axios'

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
            dialogVisible: false,
            modificatorValue:''
        }
    },
    methods: {
        createPost(post) {
            this.posts.push(post)
            this.dialogVisible = false
        },
        removePost(post){
            this.posts = this.posts.filter(p => p.id !== post.id)
        },
        showDialog() {
            this.dialogVisible = true
        },
        async fetchPosts() {
            try {
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
                console.log(responce)
            } catch (e) {
                alert('Ошибка')
            }
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