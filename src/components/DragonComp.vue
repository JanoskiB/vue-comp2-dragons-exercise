<template>
    <div class="dragons">
        <h3>{{ dragon.name }}</h3>
        <p>{{ dragon.Skills }}</p>
        <p>{{ dragon.Challenge }}</p>
        <img :src="dragon.img_url" alt="">

        <form @submit.prevent="emitMethod">
            <label for="betterName">Rename to:</label>
            <input type="text" placeholder="Better name..." id="betterName"
            v-model="newName"
            required>
            <input type="submit" value="Update name" />
        </form>

    </div>
</template>

<script>
export default {
    name: "DragonComp",
    props: {
        dragon: Object,
    },
    data(){
        return{
            newName: undefined
        }
    },

    methods: {
    emitMethod(){
     this.$emit("myCustomEvent", this.dragon.name, this.newName);
    },
  },
};

</script>

<style scoped>

* {
    margin: 0;
    padding: 0;
}

h1,
h2,
h3,
p,
img {
    margin-left: 5%;
}

h3 {
    font-size: 2rem;
}

img {
    width: 50%;
}

.dragons {
    border: 3px solid black;
    width: 40vw;
    margin: 0 auto;
    padding: 1rem;
}
</style>