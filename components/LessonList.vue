<template>
    <StackLayout>
        <Label class="h2 p-10" textWrap="true" text="Tap a product to add it to cart" />
        <ListView for='product in product' @itemTap='onItemTap'>
            <v-template>
                <StackLayout>
                    <component-to-re-render :key="`Topic: ${this.product}`" />
                    <!-- <Label :text='this.product'/> -->
                    <!-- <Label :text="`price: ${lessons.price}`"/>
                    <Label :text="`inventory: ${lessonsproduct.inventory}`"/> -->
                </StackLayout>
            </v-template>
        </ListView>
    </StackLayout>
</template>

<script>
export default {
    data() {
        return {
            product: "",
        };
    },
    methods: {
        onItemTap(event) {
            this.$emit("addProduct", event.item);
            // alert(event.item.name)
        },   
    }  
};
</script>

<style>
</style>