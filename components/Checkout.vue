<template>
    <StackLayout>
        <Label class="h2 text-center" text="Shopping Cart"/>
        <Label class="h2 text-center" text="(Tap a product to remove it)"/>
        <ListView for="product in cart" @itemTap='onItemTap'>
            <v-template>
                <StackLayout>
                    <Label>Subject: {{ product.subject }} </Label>
                    <Label>Location: {{ product.location }} </Label>
                    <Label>Price: {{ product.price }} </Label>
                    <Label>Space Available: {{ product.space}} </Label>
                </StackLayout>
            </v-template> 
        </ListView>
        <TextField hint='Name: ' v-model='name'/>
        <TextField hint='Phone Number: ' v-model='phoneNumber'/>
        <Button @tap='sendOrderToServer' text='Submit Order'/>
    </StackLayout>
</template>

<script>
export default {
    props: ['cart'],
    data() {
        return {};
    },
    methods: {
        onItemTap(event) {
            this.$emit("removeProduct", event.item);
        },
        submitOrder() {

            alert('An order is placed by ' + this.name + " at " + this.phoneNumber);
        },
        sendOrderToServer(){
            this.submitOrder();
                const newProduct = 
                {
                    "Name": this.name, "Phone Number": this.phoneNumber
                }

                fetch('https://assignment2vue.herokuapp.com/collection/order', {
                    method: 'POST', // set the HTTP method as 'POST'
                    headers: {
                    'Content-Type': 'application/json', // set the data type as JSON
                    },
                    body: JSON.stringify(newProduct), // need to stringify the JSON object
                })
                    .then(response => response.json())
                    .then(responseJSON => {
                        console.log('Success:', responseJSON);
                    });
            },
    }
};
</script>
