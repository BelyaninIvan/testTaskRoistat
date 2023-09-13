<template >
  <ul class="table">
    <li class="table__row">
      <p class="table__row-elem table__row-elem_head">
        Имя
      </p>
      <p class="table__row-elem table__row-elem_head">
        Телефон
      </p>
    </li>
    <user-item
      v-for="item in usersTable"
      :model="item"
    >
    </user-item>
  </ul>
</template>
<script>
import UserItem from './UserItem.vue';

export default {
  name: 'users-table',
  components: {
    UserItem,
  },
  props: {
    usersTable: {
      type: Array,
      default: () => [],
    },
  },
}
</script>
<style>
  .table {
    margin: 30px auto 0;
    padding: 30px 0;
    border-radius: 10px;
    list-style-type: none;
    max-width: 900px;
    width: 100%;
    background-color: rgba(134, 209, 119, 0.753);
    border-radius: 25px;
  }

  .table__row {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
    height: 100%;
  }

  .table__row-elem {
    width: 30%;
    padding: 15px;
    margin: 0;
    text-align: center;
    border: 3px green solid;
    font-size: 22px;
    word-wrap: break-word;
  }

  .table__row-elem_head {
    font-weight: 700;
  }
</style>