<template>
    <StackLayout>
        <Label class="h2 p-10" textWrap="true" text="Tap a product to add it to cart" />
        <ListView for='product in products' @itemTap='onItemTap'>
            <v-template>
                <StackLayout>
                    <Label :text='product.name'/>
                    <Label :text="`price: ${product.price}`"/>
                    <Label :text="`inventory: ${product.inventory}`"/>
                </StackLayout>
            </v-template>
        </ListView>
    </StackLayout>
</template>

<script>
export default {
    data() {
        return {
            products: [
                { name: "product 1 ", price: 5, inventory: 10 },
                { name: "product 2 ", price: 15, inventory: 10 },
                { name: "product 3 ", price: 25, inventory: 10 },
                { name: "product 4 ", price: 35, inventory: 10 }
            ],
        };
    },
    methods: {
        onItemTap(event) {
            this.$emit("addProduct", event.item);
            // alert(event.item.name)
        }
    }
};
</script>

<style>
</style>