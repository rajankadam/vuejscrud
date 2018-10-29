<template>
    <div>
        <h1>Products</h1>

        <div class="row">
          <div class="col-md-10"></div>
          <div class="col-md-2">
            <router-link :to="{ name: 'AddProduct' }" class="btn btn-primary">Create Product</router-link>
          </div>
        </div><br />

        <table class="table table-hover">
            <thead>
            <tr>
                <td>ID</td>
                <td>Title</td>
                <td>Body</td>
                
            </tr>
            </thead>

            <tbody>
                <tr v-for="item in items">
                    <td>{{ item.id }}</td>
                    <td>{{ item.title }}</td>
                    <td>{{ item.body }}</td>
                    
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                items: []
            }
        },
        
        created: function()
        {
          //alert('helo');
            this.fetchItems();
        },
        methods: {
            fetchItems()
            {
              let uri = 'https://jsonplaceholder.typicode.com/posts';
              this.axios.get(uri).then((response) => {
                  this.items = response.data;
              });
            }
        }
    }
</script>