<template>
    <div class="login-content">
        <div class="login-itemlist">
            <h1>Shopping Cart</h1>
            <table>
                <tr>
                    <th>Item</th>
                    <th>Price</th>
                    <th></th>
                </tr>
                    <itemList itemName="Bag" :itemPrice="100" :isDisabled="itsDisabled" />
                    <itemList itemName="School Supplies" :itemPrice="200" :isDisabled="itsDisabled" />
                    <itemList itemName="Lunch Box" :itemPrice="500" :isDisabled="itsDisabled" />
            </table>
        </div>
    
        <div class="login-form">
            <h3>Login</h3>
            <h5>Enter Password <br> {{ errmsg }}</h5>
            <input type="password" v-model="password">
            <button @click="login()">Login</button>
        </div>
    </div>
</template>

<script>
import itemList from '@/components/itemShop.vue'

export default {
    name: 'loginPage',
    components: {
        itemList,
    },
    
    data() {
        return {
            password: '',
            errmsg: '',
            itsDisabled: true
        }
    },

    methods: {
        login() {
            if (this.password != 'password') {
                this.errmsg = 'Wrong Password';
            } else {
                localStorage.setItem('authToken', 'true');
                this.$router.push('/shop')
            }
        }
    }
};

</script>