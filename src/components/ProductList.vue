<template>
    <div>
        <div v-for="product in products" :key="product.id">
            <h2>{{ product.title }}</h2>
            <figure>
                <img v-bind:src="product.image" />
            </figure>
            <p v-html="product.description"></p>
            <p> Price: {{ product.price }}</p>
            <p>Available Stock: {{ product.availableInventory }}</p>
            <button @click="add(product)">Add to Cart</button>
        </div>
    </div>
</template>

<script>
export default{
    name: "ProductList",
    data(){
        return{
            products: [
                
                {
                    "id": 1001,
                    "title": "Cat Food, 25lb bag",
                    "description": "A 25 pound bag of <em>irresistable</em>, organic goodness for your cat",
                    "price": 20.00,
                    "image": "cat.jpg",
                    "availableInventory": 10,
                    "rating": 2 
                },
                {
                    "id": 1002,
                    "title": "Yarn",
                    "description": "Yarn your cat can play with for a very <strong>long</strong> time!",
                    "price": 2.99,
                    "image": "yarn.jpg",
                    "availableInventory": 7,
                    "rating": 3
                },
                {
                    "id": 1003,
                    "title": "Kitty Litter",
                    "description": "Premium kitty litter for your cat",
                    "price": 11.00,
                    "image": "litter.jpg",
                    "availableInventory": 99,
                    "rating": 4
                },
                {
                    "id": 1004,
                    "title": "Cat House",
                    "description": "A place for your cat to play!",
                    "price": 7.99,
                    "image": "cat-house.jpg",
                    "availableInventory": 11,
                    "rating": 5
                },
                {
                    "id": 1005,
                    "title": "Laser Pointer",
                    "description": "Drive your cat crazy with this <em>amazing</em> product.",
                    "price": 49.99,
                    "image": "laser-pointer.jpg",
                    "availableInventory": 25,
                    "rating": 4 
                },
            ],
        }
    },
    methods: {
        add(product){
            console.log("added product", product.id);
            this.$emit('addProduct', product);
        },
    },
}
</script>
