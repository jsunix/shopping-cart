<template>
  <div class="content">
    <div class="item-list">
      <h1>Shopping Cart</h1>
      <table>
        <tr>
          <th>Item</th>
          <th>Price</th>
          <th></th>
        </tr>
          <itemList itemName="Bag" :itemPrice="100" @addCart="addToArray" />
          <itemList itemName="School Supplies" :itemPrice="200" @addCart="addToArray" />
          <itemList itemName="Lunch Box" :itemPrice="500" @addCart="addToArray" />
      </table>
    </div>
    <div class="cart-list">
      <cartList :cartList="cartList" @removeCart="removeToArray" />
    </div>
  </div>
</template>

<script>
import itemList from '@/components/itemShop.vue'
import cartList from '@/components/shopCart.vue'

export default {
  name: 'ShopApp',
  components: {
    itemList,
    cartList
  },

  data() {
    return {
      cartList: []
    }
  },

  methods: {
    addToArray(item) {
      this.cartList.push(item);
      console.log('Cart List:', this.cartList);
    },

    removeToArray(index) {
      this.cartList.splice(index, 1);
    },
  }
}
</script>
