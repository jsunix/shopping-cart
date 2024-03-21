<template>
  <div>
    <br>
    <br>

    <table>
      <tr>
        <th>Item Name</th>
        <th>Item Price</th>
        <th>Quantity</th>
        <th></th>
      </tr>
      <tr v-for="(item, index) in groupedCartList" :key="index">
        <td>{{ item.item }}</td>
        <td>{{ item.price }}</td>
        <td>{{ item.quantity }}</td>
        <td><button @click="removeToCart(index)">Remove</button></td>
      </tr>
    </table>

    <h3>Checkout Price: {{ totalPrice }}</h3>
  </div>
</template>

<script>
export default {
  name: 'cartList',
  props: ['cartList'],

  computed: {
    groupedCartList() {
      const groupedItems = {};
      this.cartList.forEach(item => {
        if (!groupedItems[item.item]) {
          groupedItems[item.item] = { ...item, quantity: 1 };
        } else {
          groupedItems[item.item].quantity++;
        }
      });
      return Object.values(groupedItems);
    },
    totalPrice() {
      return this.cartList.reduce((total, item) => total + item.price, 0);
    }
  },

  methods: {
    removeToCart(index) {
      this.$emit('removeCart', index);
    }
  }
};
</script>