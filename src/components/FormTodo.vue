<template>
    <div class="block">
        <div class="field">
            <label class="label">Nome:</label>
            <div class="control">
                <input class="input" type="text" v-model="name" placeholder="Seu nome">
            </div>
        </div>
        <div class="field">
            <label class="label">Mensagem</label>
            <div class="control">
                <textarea v-model="message" class="textarea" placeholder="Digitar mensagem"></textarea>
            </div>
        </div>
        <div class="field is-grouped">
            <div class="control">
                <button class="button is-link" @click="addComment">Enviar</button>
            </div>
            <div class="control">
                <button class="button is-link is-light" @click="clearInputs">Apagar</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                name: '',
                message: ''
            }
        },
        methods: {
            clearInputs() {
                this.name = '',
                this.message = ''
            },
            addComment() {
                if(this.message.trim() === '') {
                    return
                }
                this.$emit('add-todo', {
                    name: this.name,
                    message: this.message
                });
                this.name = '';
                this.message = '';
            },
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

</style>