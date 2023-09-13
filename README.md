# test-task

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).


createUser() {
    this.user.id = Date.now();
    if (this.selectedItem != ''){
        this.usersList.forEach(element => {
            if (element.id == this.selectedItem) {
                element.children.push(this.user);
            };
        });
    } else {
        this.usersList.push(this.user);
    }
    /* this.user.children.push(this.user.selectedItem); */
    this.$emit('create', this.user);
    this.user = {
        name: '',
        tel: ''
    };
}