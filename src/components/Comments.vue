<template>
    <FormTodo v-on:add-todo="addComment" />
    <div class="block" :key="comment.id" v-for="(comment, index) in allComments">
        <div class="block">
            <div class="box">
                <button @click="deleteComment(index)" class="delete"></button>
                <p><strong>{{ comment.name }}</strong></p>
                <p>{{ comment.message }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    import FormTodo from './FormTodo'
    export default {
        components: {
            FormTodo
        },
        data() {
            return {
                comments: []
            }
        },
        methods: {
            addComment(comment) {
                this.comments.push(comment)
            },
            deleteComment(index) {
                this.comments.splice(index, 1);
            }
        },
        computed: {
            allComments() {
                return this.comments.map(comment => ({
                    ...comment,
                    name: comment.name.trim() === '' ? 'Anônimo' : comment.name
                }))
            }
        },
        watch: {
            comments(val) {
                console.log('mudou', val);
            }
        }
    }
</script>

<style scoped>
.box button.delete {
  position: absolute;
  right: -4px;
  top: -4px;
}

.box {
  position: relative;
}

</style>