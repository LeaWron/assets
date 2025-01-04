# assets
This is a repo for typora img upload

## config
picgo configurations, need npm
### Typora install
use typora's download to get picgo commandline, then set config files like this
```json
{
  "picBed": {
    "gitee": {
      "repo": "leawron/assets", // 仓库名的格式是Gitee用户名\仓库名
      "branch": "main", // 分支名，默认是 master
      "token": "your_token", // 在gitee里生成的私人令牌 必填
      "path": "images", // 指定存储路径指的是在Gitee仓库里面的路径，我写了images，所以我的仓库下面会生成一个images目录，所有图片都会上传到这个目录下。指定存储路径不是必填项，可以不写。
      "customPath": "default",
      "customUrl": "https://gitee.com/leawron/assets/raw/main/"  // 这个就是仓库的地址，也可以默认为空
    },
    "current": "gitee",
    "uploader": "gitee", // 代表当前的上传图床
    "transformer": "path"
  },
  "picgoPlugins": {
    "picgo-plugin-gitee-uploader": true,
    "picgo-plugin-super-prefix": true
  },
  "picgo-plugin-gitee-uploader": {
    "lastSync": "2025-01-04 12:26:32"
  },
  "picgo-plugin-super-prefix": {
    "prefixFormat": "YYYY-MM-DD_HH-mm-ss_", // (定义上传文件的文件名，以时间戳命名)
    "fileFormat": ""
  } // super-prefix插件配置: prefixFormat 或者 fileFormat，注意别使用:（英文的冒号）在文件名里面，因为更新仓库到本地时会失败，windows不支持含特殊符号的文件名，
}
```

And you need two plugins to use gitee as picbed, enter where picgo is installed and run:
```bash
picgo install gitee-uploader
picgo install super-prefix
```

### npm install
If typora's downloading to get picgo commandline doesn't work, use npm
```bash
npm install picgo -g
```
Also need two same plugins
```bash
picgo install gitee-uploader
picgo install super-prefix
```
Then config picgo
```bash
picgo config uploader
```
every config can refer to config files above

Note that in this npm installing way you can't directly modify config files until you have ever configed items in commandline, or you will get error uploading

To config plugins
```bash
picgo config plugin
```
And you get choose plugin you'd like to config, then you need to "use" them
```bash
picgo use plugins
```
choose plugin you just configed, and check config files you will find it generated some items. Now you can modify this items like [Typora way](#typora-install)