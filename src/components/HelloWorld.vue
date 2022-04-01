<template>
<div>
    <div class="product">
        <div class="product-inner" v-for="item in products" :key="item.id">
            <div class="product-image-wrap">
                <img :src="item.image" class="image" />
            </div>
            <div class="product-detail">
                <h2>{{ item.name }}</h2>
                <p>{{item.price}}</p>
                <button class="btn" @click=add()>Add</button>
            </div>
            <div v-if="item.price>4000">
                <p>This is expensive</p>
            </div>
            <div v-else>
                <p>This is not expensive</p>
            </div>
            <div>
            </div>
        </div>
    </div>
        <div class="hotProducts">
            <div class="product-inner" v-for="item in hotProducts" :key="item.id">
                <div class="product-image-wrap">
                    <img :src="item.image" class="image" />
                </div>
                <div class="product-detail">
                    <h2>{{ item.name }}</h2>
                    <p>{{item.price}}</p>
                    <button class="btn" @click=add()>Add</button>
                </div>
                <div v-if="item.price>4000">
                    <p>This is expensive</p>
                </div>
                <div v-else>
                    <p>This is not expensive</p>
                </div>
            </div>
        </div>
        <div class="cart">
            <div class="product-inner" v-for="item in cart" :key="item.id">
                <div class="product-image-wrap">
                    <img :src="item.image" class="image" />
                </div>
                <div class="product-detail">
                    <h2>{{ item.name }}</h2>
                    <p>{{item.price}}</p>
                    <button class="btn" @click=remove()>Remove</button>

                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        data: {},
    },
    data() {
        return {
            cart: [],
            products: [{
                    id: 1,
                    name: "PS5",
                    price: 5555,
                    publicDate: "05-05-2021",
                    image: "https://cdn.vjshop.vn/hightech/may-choi-game/ps5/sony-ps-5-1.jpg",
                    hot: true,
                },
                {
                    id: 2,
                    name: "PS4",
                    price: 4444,
                    publicDate: "04-04-2021",
                    image: "https://gmedia.playstation.com/is/image/SIEPDC/ps4-slim-image-block-01-en-24jul20?$native--t$",
                    hot: true,
                },
                {
                    id: 3,
                    name: "PS3",
                    price: 3333,
                    publicDate: "03-03-2021",
                    image: "https://game.haloshop.vn/image/catalog/blogs/ps3-co-con-dang-mua/ps3-co-con-dang-mua-21.jpg",
                    hot: false,
                },
            ],
            paymentMethods: [{
                    text: "COD",
                    value: 1
                },
                {
                    text: "Banking",
                    value: 2
                },
                {
                    text: "Credit",
                    value: 3
                },
            ],
            selectedPayment: 2,
        };
    },
    methods: {
        add() {
            this.cart.push(this.products[0]);
            this.selectedPayment++;
        },
        remove(index) {
            this.cart.splice(index, 1);
            this.selectedPayment--;
        },
        changePayment(index) {
            this.selectedPayment = index;
        },
    },
    computed: {
        hotProducts() {
            return this.products.filter(item => item.hot);
        },
    }

};
</script>

<style>
.product,
.hotProducts, .cart {
    display: flex;
}

.hotProducts, .cart {
    margin-top: 200px;
}

.product .product-inner,
.hotProducts .product-inner, .cart .product-inner {
    width: 300px;
    height: 300px;
    border: 1px solid #ccc;
    margin: 10px;
    justify-content: space-between;
}

.product .product-inner .product-image-wrap,
.hotProducts .product-inner .product-image-wrap, .cart .product-inner .product-image-wrap {
    width: 100%;
    height: 100%;
    background-size: cover;
    background-position: center;
}

.product .product-inner .product-image-wrap img,
.hotProducts .product-inner .product-image-wrap img, .cart .product-inner .product-image-wrap img {
    width: 100%;
    height: 100%;
}
</style>
