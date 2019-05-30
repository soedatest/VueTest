<template>
  <div id="app">
    <!-- divタグ表示 -->
    <component :is="'div'"></component>
    <!-- formタグ表示 -->
    <component :is="'form'">
      <component :is="'A'"></component>
      <component 
        :is="'Input'"
        :name="dataName"
        :label="dataLabel"
        :placeholder="'入力してください'"
        v-model="form.input"
      />
      入力内容：{{ form.input }}
    </component>
    <!-- componentの動的切り替え -->
		<component :is="currentPage"></component>
		<button @click="transPage('A')">A</button>
		<button @click="transPage('B')">B</button>    
  </div>
</template>

<script>
import A from './components/A.vue'
import B from './components/B.vue'
import Input from './components/Input.vue'

export default {
  name: 'app',
  components: {
    A,
    B,
    Input
  },
  data() {
    return {
      dataName: 'simei',
      dataLabel: '氏名',
      form: {
        input: '太郎',
      },
      currentPage: ''
    }
  },
  methods: {
    transPage : function (page) {
      console.log(this.currentPage)
  		this.currentPage = page;
  	}
  }
}
</script>