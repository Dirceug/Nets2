<template>
    <div>
        <h1>
            <img :src="cancel" alt="Cancelar" id="cancel">
            Buton
            <img :src="heart" alt="Coração" id="heart">
            <img v-if="src==heart" :src="heart" alt="Coração" id="heart">
        </h1>
    </div>
</template>

<script>
export default {
    props: [
        "heart",
        "cancel"
    ]
}
</script>

<style scoped>
img {
    /* border: 2px solid black; */
    width: 20px;
    height: 20px;
    padding: 4px;
    border-radius: 15px;
}

#cancel {
    background-color: #999;
}
#cancel:hover {
    background-color: red;
}

#heart {
    background-color: #999;
}

#heart:hover {
    background-color: red;
}

img:hover{
    background-color: red;
}
</style>