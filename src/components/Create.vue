<template>
  <div class="container">
        <div class="card">
            <div class="card-header">
                <h3>Add Item</h3>
            </div>
            <div class="card-body">
                <form v-on:submit.prevent="addItem">
                  <div class="form-group">
                    <label>Name:</label>
                    <input type="text" class="form-control" v-model="item.name"/>
                  </div>
                  <div class="form-group">
                    <label>Wage:</label>
                    <input type="text" class="form-control" v-model="item.wage"/>
                  </div>

                    <div class="form-group">
                        <input type="submit" class="btn btn-primary" value="Add Item"/>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  components: {
      name: 'AddItem'
  },
  data() {
      return {
          item: {}
      }
  },
  methods: {
      addItem() {
           let uri = 'http://localhost:8089/employees/create';
            this.axios.post(uri, this.item).then((response) => {
              this.$router.push({name: 'Index'});
            });
        }
    }
}
</script>