## 作用
修改vue-template-admin,兼容django-rest-framework的 simple-jwt认证
## 修改  
1.删除util/request.js 20000code判断  
2.修改util/request.js token头  
3.修改store/modules/user.js token key为access  
4.关闭mock  
## 运行
```
npm run dev
```
## drf相关
安装 simplejwt
```
pip install djangorestframework-simplejwt
```
urls.py中添加token
```
from django.urls import path, include

from rest_framework.routers import  DefaultRouter
from rest_framework_simplejwt.views import (
    TokenObtainPairView,
    TokenRefreshView,
)
from .views import UserInfoViewset

route = DefaultRouter()
route.register('UserInfo', UserInfoViewset, basename='UserInfo')

urlpatterns = [
    path('login', TokenObtainPairView.as_view(), name='token_login'),
    path('', include(route.urls))
]
```
view.py 添加 getinfo视图
```
class UserInfoViewset(viewsets.ViewSet):
    permission_classes = (permissions.IsAuthenticated,)
    def list(self, request, *args, **kwargs):
        data = {
            "username": "admin",
            "name": "admin"
        }
        return response.Response(data)
```
