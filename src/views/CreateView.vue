<template>
  <div class="card col-6 m-auto">
    <form action="" class="p-2">
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label"
          >name address</label
        >
        <input
          class="form-control"
          id="exampleFormControlInput1"
          placeholder="name"
          v-model="name"
        />
      </div>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label">job</label>
        <input
          class="form-control"
          id="exampleFormControlInput1"
          placeholder="job"
          v-model="job"
        />
      </div>
      <button class="btn btn-info text-white"  @click="registrar()" >
        Registrar
      </button>
    </form>
  </div>
  <div
    class="alert alert-primary mt-2 col-5 m-auto"
    role="alert"
    v-if="menssage"
  >
    yeeesssssss!!!
  </div>
</template>
<script>
import axios from "axios";
export default {
  data: () => ({
    name: "",
    job: "",
    menssage: false,
  }),
  methods: {

    registrar() {
      const r = {
        name: this.name,
        job: this.job,
      };
      return new Promise((resolve, reject) => {
        axios
          .post("api/users", r)
          .then((res) => {
            resolve(res.data);
            this.menssage = true;
            setTimeout(() => {
              this.menssage = false;
            }, 3000);
          })
          .catch(() => {
            reject();
          });
      });
    },
  },
};
</script>