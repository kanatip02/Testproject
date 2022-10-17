<template>
  <div>
    <h1 style="background-color:red">ทั้งหมด</h1><br>  
    {{ data1 }}
  </div>
  <div>
    <h1 style="background-color:blue">ในอดีต</h1><br>
    {{ data2 }}
  </div>
  <div>
    <h1 style="background-color:green">กำลังจะถึง</h1><br>
    {{ data3 }}
  </div>
</template>

<script>
import { HTTP } from "@/axios.js";
export default {
  data() {
    return {
      data1: "",
      data2: "",
      data3: "",
    };
  },
  mounted() {
    this.getdata1();
    this.getdata2();
    this.getdata3();
  },
  methods: {
    async getdata1() {
      await HTTP.get(`v5/launches`)
        .then((res) => {
          {
            this.data1 = res.data;
          }
        })
        .catch((e) => {
          console.log(e);
        });
    },
    async getdata2() {
      await HTTP.get(`v5/launches/past`)
        .then((res) => {
          {
            this.data2 = res.data;
          }
        })
        .catch((e) => {
          console.log(e);
        });
    },
    async getdata3() {
      await HTTP.get(`v5/launches/upcoming`)
        .then((res) => {
          {
            this.data3 = res.data;
          }
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
};
</script>

<style scoped></style>
