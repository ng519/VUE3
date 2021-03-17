<template>
    <StackLayout>
        <Label class="h2 p-10" textWrap="true" text="Tap a product to add it to cart" />
        <Button @tap='Load' text='Load Lessons'/>
        <Label :text="`Topic: ${this.product[0]}`"/>
        <Label>Hi: {{ testing }}</Label>
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
        forceRerender() {
            this.product
        },
        Load() {
            fetch('https://assignment2vue.herokuapp.com/collection/Lessons').then(function (response) {
            response.json().then(
                function (json) {
                    // note that we used 'store.product' instead of 'this.product'
                    
                    this.product = json;
                })
                
            })
                
        }     
    }  
};
</script>

<style>
</style>