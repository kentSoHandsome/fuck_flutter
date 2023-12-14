# fuck_flutter
# flutter_dog
# 踩坑记录，MMP

## web
### web build 和 开发模式下run的小坑。
run 或者 build的时候，加一个命令。

第一个命令：```--web-renderer=html```  web可以加载网络图片。

在build环境下部署，可能会出现跨域问题。如果后台解决了跨域问题，那么前端build的时候加上这个命令可以解决跨域问题。

第二个命令：```--no-tree-shake-icons``` web上图片不加载缩略图，不丢帧。

示例：
``` dart
flutter build web --release --web-renderer=html --no-tree-shake-icons
```
如果是用Android studio开发，在最上边有一个配置。如图

<img width="258" alt="image" src="https://github.com/kentSoHandsome/flutter_dog/assets/152961018/a0ba0979-1e54-4825-84f7-4f12bb1615f8">

添加参数即可在Android studio里run的时候自动加上。

<img width="824" alt="image" src="https://github.com/kentSoHandsome/flutter_dog/assets/152961018/db64cf58-4611-4b33-9966-cba891d7b6c6">


### web build
打包web发布的时候，踩坑。部署成功后，访问127.0.0.1:端口，就是正常，当访问IP+端口的时候，web控制台一直报错:```Uncaught (in promise) null```。

解决方案：创建项目的时候用的是flutter3.16.0创建的，然后后面用flutter 3.16.3 创建项目，再把老项目全部迁移到新项目，包括配置文件，资源文件，class。在重新build部署，一切正常。

```
PS:我怀疑是flutter的问题，哪怕不断地切换flutter版本都没用，还是promise问题，然后用其他版本的flutter创建项目，在进行项目copy，就没任何问题了。
```

### 题外话
在build下的web目录下，运行一个本地服务。

```
flutter run -d web-server --web-port=45638 --web-hostname=0.0.0.0
```

也可以使用Mac自带的Python服务。

第一个终端
```
python3 -m http.server 8085
```

第二个终端，进入build的web项目里。执行:
```
npx http-server
```



