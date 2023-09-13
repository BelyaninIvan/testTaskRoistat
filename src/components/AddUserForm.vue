<template>
  <form class="form" @submit.prevent="createUser">

    <label for="userName" class="form__label">Введите имя:</label>
    <my-input
      v-model="user.name"
      type-input="text"
      name="userName"
      placeholder="Введите имя"
      min-length="3"
      max-length="25"
      required
    />

    <label for="userPhone" class="form__label">Введите телефон:</label>
    <my-input
      v-model="user.tel"
      type-input="tel"
      name="userPhone"
      placeholder="Введите телефон"
      max-length="11"
      required
    />

    <label for="userMentor" class="form__label">Выберите начальника:</label>
    <my-select
      :options="usersList"
      v-model="selectedItem"
      name="userMentor"
    />

    <my-button
      button-type="submit"
    >
      Добавить
    </my-button>

  </form>
</template>
<script>
import MyInput from './UI/MyInput.vue';
import MySelect from './UI/MySelect.vue';
import MyButton from './UI/MyButton.vue';

export default {
  name: 'add-user-form',
  components: {
    MyInput,
    MySelect,
    MyButton,
  },
  props: {
    usersList: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      user: {
        id: '',
        name: '',
        tel: '',
        children: [],
      },
      selectedItem: '',
    }
  },
  methods: {
    createUser() {
      this.user.id = Date.now();
      if (this.selectedItem != '') {
        this.usersList.forEach(element => {
          if (element.id == this.selectedItem) {
            element.children.push(this.user);
          };
        });
      } else {
        this.usersList.push(this.user);
      }
      this.$emit('create', this.user);
      this.user = {
        name: '',
        tel: ''
      };
    },
  },
}
</script>
<style scoped>
  .form {
    display: flex;
    flex-direction: column;
    row-gap: 15px;
  }

  .form__label {
    margin: 0;
    margin-left: 15px;
    color: white;
    font-weight: 700;
  }
</style>