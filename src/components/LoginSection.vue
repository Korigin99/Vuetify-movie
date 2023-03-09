<template>
  <v-container>
    <v-col class="title">
      <v-icon icon="mdi-vuetify" />
      <span>Vue + Vuetify Giude</span>
    </v-col>
    <v-alert
      title="vuetify"
      text="Let's try Vue.js and Vuetify"
      class="v-alert"
    ></v-alert>
    <v-col class="input-section">
      <form @submit.prevent="addItem">
        <input
          v-model="i_title"
          type="text"
          placeholder="title"
          maxlength="10"
        />
        <input
          v-model="i_subtitle"
          type="text"
          placeholder="subtitle"
          maxlength="30"
        />
        <v-btn
          variant="plain"
          @click="addItem"
          style="border: 1px solid #efefef"
          >Write</v-btn
        >
      </form>
    </v-col>
    <v-col class="input_result">
      <p>Title : {{ i_title }}</p>
      <p>SubTitle : {{ i_subtitle }}</p>
    </v-col>
    <v-list lines="one">
      <v-list-item
        v-for="item in items"
        :key="item.title"
        :title="item.title"
        :subtitle="item.subtitle"
      >
        <v-btn @click="removeItem(item)">X</v-btn>
      </v-list-item>
    </v-list>
    <v-col>
      <form @submit.prevent="doSearch">
        <input type="text" placeholder="영화 제목" v-model="movie_title" />
        <v-btn icon="search" @click="doSearch">검색</v-btn>
      </form>
    </v-col>
    <v-col>
      <v-table>
        <thead>
          <th>제목</th>
          <th>개봉일</th>
        </thead>
        <tbody>
          <tr></tr>
        </tbody>
      </v-table>
    </v-col>
  </v-container>
</template>

<script>


export default {
  data() {
    return {
      i_title: "",
      i_subtitle: "",
      items: [{ title: "test", subtitle: "test2" }],
    };
  },
  methods: {
    addItem() {
      this.items.push({ title: this.i_title, subtitle: this.i_subtitle });
      (this.i_title = ""), (this.i_subtitle = "");
    },
    removeItem(item) {
      this.items = this.items.filter((i) => i !== item);
    },
    doSearch() {
      let m_title = this.movie_title;
      console.log(m_title)
      
      this.$axios.get('https://openapi.naver.com/').
      then((res) => {
        console.log(res)
      })

    },
  },
};
</script>

<style>
.title {
  text-align: center;
  font-size: 30px;
  font-weight: 700;
}

.input-section,
.input-result,
.input-section form {
  width: 600px;
  display: flex;
  justify-content: space-between;
}

.input-result p {
  overflow: hidden;
}

.input-section input {
  padding: 10px;
  border: 1px solid #efefef;
  border-radius: 5px;
}

.v-list-item__content {
  display: flex;
  justify-content: space-between;
}

.v-list-item__content:nth-child(n) {
  overflow: hidden;
}
</style>