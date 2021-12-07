<template>
  <div class="container">
    <div class="row justify-content-center mt-5">
      <div class="col-md-8">
        <div class="card">
          <div class="card-header">Data Level</div>

          <div class="card-body">
            <div class="form-group">
              <div class="table-responsive">
                <table class="table table table-striped">
                  <thead class="thead-light">
                    <tr>
                    <th>Nama Level</th>
                    <th>Aksi</th>
                  </tr>
                  </thead>
                  
                  <tr v-for="item in levels" :key="item.id">
                    <td>{{ item.namalevel }}</td>
                    <td>
                      <i class="fas fa-edit blue"></i>
                      <i class="fas fa-trash-alt red"></i>
                    </td>
                  </tr>
                </table>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      levels: {}
    };
  },
  methods: {
    loadData() {
      this.$Progress.start();
      axios.get("api/ambildatalevel").then(({ data }) => (this.levels = data));
      this.$Progress.finish();
    }
  },
  created() {
    this.loadData();
  }
};
</script>
