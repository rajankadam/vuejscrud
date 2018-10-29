<template>
  <div>
    <h1>Create An Product</h1>
    <form v-on:submit.prevent="addProduct">
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label>Title:</label>
            <input type="text" class="form-control" v-model="item.title">
          </div>
        </div>
        </div>
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>Body:</label>
              <input type="text" class="form-control col-md-6" v-model="item.body" />
             
            </div>
          </div>
        </div><br />
        <div class="form-group">
          <button class="btn btn-primary">Add Product</button>
        </div>
    </form>
  </div>
</template>
<script>
  export default {
    data(){
        return{
          item:{}
        }
    },
    methods: {
      addProduct(){
        let uri = 'https://jsonplaceholder.typicode.com/posts';
        this.axios.post(uri, this.item).then((response) => {
          this.$router.push({name: 'Product'})
        })
    }
  }
}
</script>