<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li>
        <a
          href="https://vuejs.org"
          target="_blank"
        >
          Core Docs
        </a>
      </li>
      <li>
        <a
          href="https://forum.vuejs.org"
          target="_blank"
        >
          Forum
        </a>
      </li>
      <li>
        <a
          href="https://chat.vuejs.org"
          target="_blank"
        >
          Community Chat
        </a>
      </li>
      <li>
        <a
          href="https://twitter.com/vuejs"
          target="_blank"
        >
          Twitter
        </a>
      </li>
      <br>
      <li>
        <a
          href="http://vuejs-templates.github.io/webpack/"
          target="_blank"
        >
          Docs for This Template
        </a>
      </li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li>
        <a
          href="http://router.vuejs.org/"
          target="_blank"
        >
          vue-router
        </a>
      </li>
      <li>
        <a
          href="http://vuex.vuejs.org/"
          target="_blank"
        >
          vuex
        </a>
      </li>
      <li>
        <a
          href="http://vue-loader.vuejs.org/"
          target="_blank"
        >
          vue-loader
        </a>
      </li>
      <li>
        <a
          href="https://github.com/vuejs/awesome-vue"
          target="_blank"
        >
          awesome-vue
        </a>
      </li>
    </ul>
    <ul>
      <li>
        <table>
          <tr v-for="item in emps" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.userid}}</td>
            <td>{{item.pwd}}</td>
            <td>{{item.name}}</td>
            <td>{{item.createDate}}</td>
            <td>{{item.operator}}</td>
          </tr>
        </table>
      </li>
    </ul>
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  created: function(){
    this.$axios({
      method: 'post',
      //headers: {'Contentt-TType': 'application/json'},
      url: '/api/testMybatisConcat;jsessionid=2CD685323B64B103E392A3D21F79ADD0',
      //data: this.qs.stringify([{"operator":"admin"}])
      data: [{'operator':'admin'}]
    }).then(resp=>{
      if(resp.status===200){
        console.log(resp)
        this.emps = resp.data.data
      }else{
        console.log('response code is '+resp.status)
        console.log(resp.data)
      }
    }).catch(err=>console.log(err))
  },
  data () {
    return {
      emps: [],
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
