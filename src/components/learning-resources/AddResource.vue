<template>
            <base-dialog v-if="inputIsInvalid" title="Invalid Input!" @close="confirmError">
               <template #default>
                <p>At least one input field is invalid..</p>
                <p>Enter at least a few characters</p>
               </template>
               <template #actions>
                <base-button @click="confirmError">Okay</base-button>
            </template>
        </base-dialog>
    <base-card>
    <form @submit.prevent="submitForm">
        <div>
            <label for="title">Title:</label>
            <input id="title" type="text" ref="title">
        </div>
       
        <div>
            <label for="descr">Description:</label>
            <textarea name="descr" id="descr" rows="3" ref="description"></textarea>
        </div>

        <div>
            <label for="link">Link:</label>
            <input id="link" type="url" ref="link">
        </div>

        <div>
            <base-button id="btn" type="submit">Add Resource</base-button>
        </div> 
    </form>
</base-card>
</template>

<script>

export default {
    inject: ['addResource'],
    data() {
        return {
            title: '',
            description: '',
            link: '',
            inputIsInvalid: false
        }
    },
    methods: {
        submitForm() {
            const enteredTitle = this.$refs.title.value
            const enteredDescription = this.$refs.description.value
            const enteredUrl = this.$refs.link.value

            
            if (enteredTitle.trim() === '' || enteredDescription.trim() === '' || enteredUrl.trim() === '') {
                this.inputIsInvalid = true
                return
            }

            this.addResource(enteredTitle, enteredDescription, enteredUrl)  
        },
        confirmError() {
            this.inputIsInvalid = false
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