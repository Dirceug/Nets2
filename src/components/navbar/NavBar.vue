<template>
    <div class="container">
        <a href="/">
            <img :src="logo" :alt="app_name" id="logo">
        </a>
        <div id="whish">
            <a href="/desejos">
            <img :src="heart" :alt="app_name" id="heart">
                <h2 class="wishlist">
                    Whishlist
                </h2>
            </a>
        </div>
        <img :src="user" :alt="app_name" id="user">
        <font-awesome-icon icon="fa-solid fa-user-secret" />
        <font-awesome-icon icon="fa-solid fa-circle-user" />
        <font-awesome-icon icon="fa-regular fa-heart" />
    </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faUserSecret } from '@fortawesome/free-solid-svg-icons'

library.add(faUserSecret)

export default {
    components: {
        
    },
    props: [
        "logo",
        "app_name",
        "heart",
        "user"
    ]
}

</script>

<style scoped>
.container {
    background-color: #5a2d82;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding: 5px;
    padding-right: 30px;
}

.logo {
    /* padding: 5px; */
    padding: 20px;
    margin: auto;
    margin-left: 0;
    color: white;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    /* font-weight: bold; */
}

.wishlist {
    color: white;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-size: 18px;
    margin: auto;
    margin-right: 0;
}

a {
    display: flex;
}

img {
    /* border: 2px solid black; */
    padding: 1px;
    margin: auto;
    margin-left: 0;
    padding-left: 30px;
}

h2 {
    font-weight: 300;
    font-size: 16px;
}

#whish {
    display: flex;
    position: absolute;
    right: 100px;
}


#heart {
    padding-right: 15px;
}

#user {
    margin: auto;
    margin-right: 0;
}

</style>