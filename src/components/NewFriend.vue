<template>
    <form @submit.prevent="submitData">
        <div>
            <label>Name</label>
            <input type="text" v-model="enterName"/>
        </div>
        <div>
            <label>Phone</label>
            <input type="tel" v-model="enterPhone"/>
        </div>
        <div>
            <label>Email</label>
            <input type="email" v-model="enterEmail"/>
        </div>
        <div>
            <button>Add contact</button>
        </div>
    </form>
    
</template>

<script>
export default {
    emits: ['add-friend'],
    data() {
        return {
            enterPhone: '',
            enterName: '',
            enterEmail: ''
        }
    },
    methods: {
        submitData () {
            this.$emit('add-friend', this.enterName, this.enterPhone, this.enterEmail)
        }
    }
}
</script>
