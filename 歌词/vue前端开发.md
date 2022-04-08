vue前端开发

element ui配置

1. 安装

   ```
   npm i element-ui -S 
   ```

2. 项目引入element ui

   main.js 

   ```vue
   import ElementUI from 'element-ui'
   import 'element-ui/lib/theme-chalk/index.css'
   
   ```

3. 使用element ui

   Login.vue

   ```vue
   <template>
     <el-card>
         用户名:<input type="text" v-model="loginForm.username" placeholder="请输入用户名"/>
         <br><br>
         密码： <input type="password" v-model="loginForm.password" placeholder="请输入密码"/>
         <br><br>
         <button v-on:click="login">登录</button>
     </el-card>
   </template>
   
   <script>
    
     export default {
       name: 'Login',
       data () {
         return {
           loginForm: {
             username: '',
             password: ''
           },
           responseResult: []
         }
       },
       methods: {
         login () {
           this.$axios
             .post('/login', {
               username: this.loginForm.username,
               password: this.loginForm.password
             })
             .then(successResponse => {
               if (successResponse.data.code === 200) {
                 this.$router.replace({path: '/index'})
               }
             })
             .catch(failResponse => {
             })
         }
       }
     }
   </script>
   
   
   ```

   