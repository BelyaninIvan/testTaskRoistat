<template>
  <div id="app" class="app">
    <section class="content">
      <my-button
        button-type="button"
        @click="openDialog"
      >
        Добавить
      </my-button>

      <users-table
        :usersTable="users"
      >
      </users-table>
    </section>

    <my-dialog
      :show.sync="dialogVisible"
      modal-title="Добавить пользователя"
    >
      <add-user-form 
        :users-list="users"
        :users-select-list="selectUsers"
        @create="createUser"
      />
    </my-dialog>
  </div>
</template>

<script>
import MyButton from './components/UI/MyButton.vue';
import MyDialog from './components/UI/MyDialog.vue';
import UsersTable from './components/UsersTable.vue';
import AddUserForm from './components/AddUserForm.vue';

export default {
  name: 'App',
  components: {
    MyButton,
    UsersTable,
    AddUserForm,
    MyDialog,
  },
  data() {
    return {
      users: [
        {
          id: 1,
          name: 'Иван',
          tel: '+79379661986',
          children: [
            {
              id: 12,
              name: 'Иванесунс',
              tel: '+79379661986',
              children: [
              {
                id: 125,
                name: 'Иванесунсенс',
                tel: '+79379661986',
                children: [],
              }
              ],
            },
          ],
        },
        {
          id: 2,
          name: 'Дмитрий',
          tel: '+79379661986',
          children: [],
        },
        {
          id: 3,
          name: 'Евгений',
          tel: '+79379661986',
          children: [],
        },
        {
          id: 4,
          name: 'Саша',
          tel: '+79379661986',
          children: [],
        },
      ],
      selectUsers: [
      {
          id: 1,
          name: 'Иван',
          tel: '+79379661986',
          children: [],
        },
        {
          id: 12,
          name: 'Иванесунс',
          tel: '+79379661986',
          children: [],
        },
        {
          id: 125,
          name: 'Иванесунсенс',
          tel: '+79379661986',
          children: [],
        },
        {
          id: 2,
          name: 'Дмитрий',
          tel: '+79379661986',
          children: [],
        },
        {
          id: 3,
          name: 'Евгений',
          tel: '+79379661986',
          children: [],
        },
        {
          id: 4,
          name: 'Саша',
          tel: '+79379661986',
          children: [],
        },
      ],
      dialogVisible: false,
    }
  },
  methods: {
    openDialog() {
      this.dialogVisible = true;
    },
    createUser(user) {
      this.selectUsers.push(user);
      this.user = '';
      this.dialogVisible = false;
      this.saveUsers();
    },
    saveUsers() {
      const parsed = JSON.stringify(this.users);
      localStorage.setItem('users', parsed);
    }
  },
  mounted() {
    if (localStorage.getItem('users')) {
      try {
        this.users = JSON.parse(localStorage.getItem('users'));
      } catch(e) {
        localStorage.removeItem('users');
      }
    }
  },
}
</script>

<style>
.app {
  margin: 0;
  padding: 50px;
  min-height: 100vh;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: rgb(140,161,255);
  background: linear-gradient(90deg, rgba(140,161,255,1) 0%, rgba(194,200,144,1) 50%, rgba(140,161,255,1) 100%);
}

.content {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.item {
  cursor: pointer;
  line-height: 1.5;
}
.bold {
  font-weight: bold;
}
</style>
