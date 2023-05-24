<template>
    <li>
        <h2> {{ name }}{{ isFavorite? "(Favorite)": "" }}</h2>
        <button @click="toggleDetails">Show Details</button>
        <button @click="toggleFavorite">Show Favorites</button>
        <ul v-if="detailAreVisible">
            <li><strong>Phone:</strong>{{ phone }}</li>
            <li><strong>Email:</strong>{{ email }}</li>
        </ul>
    </li>
</template>

<script>
export default {
    props:{
        id: {
            type:String,
            required:true
        },
        name: {
            type: String,
            required: true
        },
        phone: {
            type: String,
            required: true
        },
        email: {
            type: String,
            required: true
        },
        isFavorite: {
            type: Boolean,
            required: false,
            default: false
        }
    },
    data() {
        return {
            detailAreVisible: false,
        }
    },
    emits: ['toggle-favorite'],
    methods: {
        toggleDetails() {
            return this.detailAreVisible = !this.detailAreVisible
        },
        toggleFavorite() {
            this.$emit('toggle-favorite',this.id)
        }

    }   
}
</script>