<template>
    <form @submit.prevent="handleSubmit" :class="{active: isSearchActive}">
        <diV>
            <button>

                <img src="~/assets/loupe.svg" />
            </button>
            <input placeholder="Search something you want to learn" v-model="search" />
        </div> 
    </form>
</template>

<script>
export default {
    props: {
        isSearchActive: Boolean,
        animationIsComplete: Boolean
    },
    data: function(){
        return {
            search: "",
        }
    }, methods: {
        handleSubmit: function(){
            this.$emit('toggle')

            this.$router.push({path: '/search', query: {q: this.search}});

        },
    }
}
</script>

<style>
form {
    height: 200px;
    background: var(--main-color);
    width: 100%;
    position: absolute;
    top: 0;
    transform: translateY(-100%);
    transition: .2s;
    display: flex;
    justify-content: center;
    align-items: center;
}

form.active {
    transform: translateY(0);
}

form div {
    width: 90%;
    position: relative;
    margin-top: 25px;

}

button {
    position: absolute;
    right: 15px;
    top: 0;
    bottom: 0;
    margin: auto;
    width: 20px;
    height: 20px;
    background: none;
    border: none;
    cursor: pointer;
    opacity: .5;
}
button:hover {
    opacity: 1;
}



form div input {
    width: 100%;
    height: 50px;
    border: 1px solid #eee;
    border-radius: 5px;
    padding-left: 10px;
    padding-right: 50px;
}

form div input:focus {
    outline: none;
}

@media(min-width: 700px){
    form div input {
        font-size: 18px;
        padding-left: 20px;
    }
}
</style>