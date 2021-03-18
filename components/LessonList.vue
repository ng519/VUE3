<template>
    <StackLayout>
        <Label class="h2 p-10" textWrap="true" text="Tap a product to add it to cart" />
        <ListView for='product in products' @itemTap='onItemTap'>
            <v-template>
                <StackLayout>
                    <Label>Subject: {{ product.subject }} </Label>
                    <Label>Location: {{ product.location }} </Label>
                    <Label>Price: {{ product.price }} </Label>
                    <Label>Space Available: {{ product.space }} </Label>
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
                {id: 1001, subject: "Math", location: "Blackbird Down", price: 20, space: 10},
                {id: 1002, subject: "English", location: "English Street", price: 17, space: 10},
                {id: 1003, subject: "Physics", location: "Paradise East", price: 25, space: 10},
                {id: 1004, subject: "Art", location: "Dene Park", price: 23, space: 10},
                {id: 1005, subject: "Computer Studies", location: "Mallow Walk", price: 20, space: 10},
                ],
        };
    },
    methods: {
        onItemTap(event) {
            this.$emit("addProduct", event.item);
            // alert(event.item.name)
            event.item.space -= 1;
        }
    }
};
</script>

<style>
</style>