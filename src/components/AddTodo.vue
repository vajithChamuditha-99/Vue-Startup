<template>
    <div>
        <form @submit= "addTodo"> 
            <input type='text' v-model= "title" name="title" placeholder="Add Todo...">
            <input type='submit' value="Submit" class="btn">

        </form>
    </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';


export default {
    name: "AddTodo",
    data(){
        return{
            title: ''
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                id: uuidv4(),
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', newTodo);

            this.title=''
        }
    }
}
</script>

<style scoped>
    form{
        background-color: darkkhaki;
        padding: 8px;
    }

    input[type='submit']{
        flex: 50px;
        padding: 6px 40px;
        
    }

    input[type='text']{
        flex: 50px;
        padding: 5px 60px;
        
    }
</style>