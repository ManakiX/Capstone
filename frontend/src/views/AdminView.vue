<template>
  <div class="admin">
    <div class="productCRUD">
      <h2>Products Table</h2>
      <table class="table table-hover table-striped table-dark">
        <thead>
          <tr>
            <th>Name</th>
            <th>Description</th>
            <th>Price</th>
            <th>Edit/Delete</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="product in products" :key="product">
            <td>{{ product.prodName }}</td>
            <td>{{ product.prodDescription }}</td>
            <td>R{{ product.price }}</td>
            <td>
              <div class="btn-group">
                <UpdateProduct :product="product" :productId="product.id" />
                <button class="btn btn-danger" v-on:click="deleteProduct(product.id)">Delete</button>
              </div>
            </td>
          </tr>
        </tbody>
        <tfoot>
          <tr>
            <td></td>
            <td></td>
            <td></td>
            <td class="d-flex justify-content-center">
              <AddProduct />
            </td>
          </tr>
        </tfoot>
      </table>
    </div>
    <div class="userCRUD">
      <table class="table table-hover table-striped table-dark">
        <thead>
          <tr>
            <th>Name</th>
            <th>Surname</th>
            <th>Email Address</th>
            <th>Role</th>
            <th>Profile Image URL</th>
            <th>Edit/Delete</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in users" :key="user">
            <td>{{ user.firstName }}</td>
            <td>{{ user.lastName }}</td>
            <td>{{ user.emailAdd }}</td>
            <td>{{ user.userRole }}</td>
            <td>{{ user.userProfile }}</td>
            <td>
              <div class="btn-group">
                <UpdateUser :user="user" :userId="user.userID" />
                <button class="btn btn-danger">Delete</button>
              </div>
            </td>
          </tr>
        </tbody>
        <tfoot>
          <tr>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
          </tr>
        </tfoot>
      </table>
    </div>
  </div>
</template>

<script>
import UpdateProduct from '../components/UpdateProduct.vue'
import AddProduct from '../components/AddProduct.vue'
import { useStore } from 'vuex';
import { computed } from '@vue/runtime-core';

export default {
  setup() {
    const store = useStore();
    store.dispatch('fetchProducts');
    store.dispatch('fetchUsers');

    const user = computed(() => store.state.user);
    const products = computed(() => store.state.products);
    const users = computed(() => store.state.users);

    const deleteProduct = async (id) => {
      store.dispatch('deleteProduct', id);
      store.dispatch('fetchProducts');
      location.reload();
    }

    return {
      products,
      users,
      user,
      deleteProduct,
    }
  },
  components: {
    UpdateProduct,
    AddProduct,
  },
  props: ['product', 'productId']
}
</script>

<style scoped>
  .admin {
    display: flex;
    justify-content: space-between;
    margin: 20px;
    position: relative;
    background-image: url('https://i.postimg.cc/4ymwDgqT/Archie-Vable-Gaming-Logo.png');
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    font-family: Arial, sans-serif;
    margin: 0;
    z-index: 1;
  }

  .productCRUD {
    width: 70%;
    padding: 20px;
    background-color: #f8f9fa;
    border-radius: 5px;
  }

  .userCRUD {
    width: 28%;
    padding: 20px;
    background-color: #f8f9fa;
    border-radius: 5px;
  }

  h2 {
    font-size: 28px;
    margin-bottom: 20px;
  }

  table {
    width: 100%;
    margin-bottom: 50px;
    border-collapse: collapse;
  }

  th {
    font-weight: bold;
    text-transform: uppercase;
    border-bottom: 2px solid #dee2e6;
    padding: 10px;
    text-align: left;
  }

  td {
    border-bottom: 1px solid #dee2e6;
    padding: 10px;
    vertical-align: middle;
  }

  tbody tr:hover {
    background-color: #f2f2f2;
  }

  thead {
    background-color: #343a40;
    color: #fff;
  }

  tfoot {
    background-color: #343a40;
    color: #fff;
  }

  tfoot td {
    padding: 20px;
  }

  .btn-group {
    display: flex;
    gap: 10px;
  }

  .btn-danger {
    background-color: #dc3545;
    border: none;
    color: #fff;
    padding: 5px 10px;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.2s ease-in-out;
  }

  .btn-danger:hover {
    background-color: #c82333;
  }

  .d-flex {
    display: flex;
  }

  .justify-content-center {
    justify-content: center;
  }

  .add-product-btn {
    background-color: #28a745;
    border: none;
    color: #fff;
    padding: 10px 20px;
    font-size: 18px;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.2s ease-in-out;
  }

  .add-product-btn:hover {
    background-color: #218838;
  }

  .img-fluid {
    max-width: 100%;
    height: auto;
  }

  .product-image {
    width: 80px;
    height: 80px;
    margin-right: 10px;
    overflow: hidden;
    border-radius: 50%;
  }

  .product-image img {
    object-fit: cover;
    height: 100%;
    width: 100%;
  }

  .btn-outline-secondary {
    border-color: #6c757d;
    color: #6c757d;
    transition: all 0.2s ease-in-out;
  }

  .btn-outline-secondary:hover {
    background-color: #6c757d;
    color: #fff;
  }

  .form-control {
    border-color: #dee2e6;
  }

  .form-control:focus {
    border-color: #6c757d;
    box-shadow: 0 0 0 0.2rem rgba(108, 117, 125, 0.25);
  }
</style>