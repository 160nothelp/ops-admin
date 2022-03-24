## 作用
修改vue-template-admin,兼容django-rest-framework的 simple-jwt登录
## 修改
1.删除util/request.js 20000code判断 
2.修改util/request.js token头
3.修改store/modules/user.js token key为access
4.关闭mock
