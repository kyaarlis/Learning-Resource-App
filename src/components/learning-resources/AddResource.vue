<template>
    <base-card>
    <form @submit.prevent="submitForm">
        <div>
            <label for="title">Title:</label>
            <input id="title" type="text" v-model="title">
        </div>
       
        <div>
            <label for="descr">Description:</label>
            <textarea name="descr" id="descr" rows="3" v-model="description"></textarea>
        </div>

        <div>
            <label for="link">Link:</label>
            <input id="link" type="url" v-model="link">
        </div>

        <div>
            <base-button id="btn" type="submit">Add Resource</base-button>
        </div>
    </form>
</base-card>
</template>

<script>
export default {
    data() {
        return {
            title: '',
            description: '',
            link: ''
        }
    },
    methods: {
        submitForm() {
            this.$emit('add-resource', this.title, this.description, this.link)
        }
    }
}
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}

#btn {
    margin-top: 10px;
}
</style>