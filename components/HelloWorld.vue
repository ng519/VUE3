<template>
    <Page style="background-color: azure">
        <ActionBar title="Pet Shop" />
        <Label text="Welcome to the Pet Shop!" class="h2" />
        <TabView>
            <!-- Product List Part -->
            <TabViewItem title="Product List" class="h2 text-capitalize">
                <ProductList @addProduct="addToCart" />
            </TabViewItem>
            <!-- Checkout Part -->
            <TabViewItem title="Check out" class="h2 text-capitalize">
                <Checkout :cart="cart" @removeProduct="removeFromCart"/>
            </TabViewItem>
        </TabView>
    </Page>
</template>

<script>
    import LessonList from "./LessonList"; // Import the component
    import Checkout from "./Checkout";

    export default {
        data() {
            return {
                cart:[],
            };
        },
        components: {
            LessonList, Checkout
            },
        methods: {
            addToCart(product){
                this.cart.push(product);
                //alert ("Parent: Added to cart: " + product.name);
            },
            removeFromCart(product){
                for (let i=0; i<this.cart.length; i++) {
                    if (this.cart[i] == product) this.cart.splice(i,1)
                }
            },
        },
    };
</script>

<style>
</style>