### 03-03 国内被墙了，已支持设置代理，或者使用海外服务器
### 03-01 更新，替换ChatGPT接口了！速度超快的！
### 持续优化中，喜欢的同学给个🌟关注一下
### 声明：此项目请仅用于学习和体验技术，勿做商用

### 一、介绍
- 使用
  - 用作公众号被动回复。(本项目支持微信被动时限15s，一般问题不会超时，超时后端会缓存答案，可以稍后重新提问立即返回)
  - 可以直接api调用。(忽略下边有关公众号的配置即可)
- 免费吗？不算，`OpenAI`账号赠送18$，限期使用。 $0.002 / 1000 tokens，每次花费已经打印在日志里。（暂时没做上下文）
- 风险。依托于公众号存在一定风险。 我已加了[敏感词检测](https://github.com/tomatocuke/sieve) ，但不清楚微信具体机制此举是否有效。
- 体验。关注公众号`杠点杠`尝试提问，这仅是个人娱乐号，不推送。


### 部署
1. 获取`API_KEY`。[OpenAI](https://beta.openai.com/account/api-keys) （如果访问被拒绝，注意全局代理，打开调试，Application清除LocalStorage后刷新，实测可以）
2. 获取微信公众号`令牌Token`：[微信公众平台](https://mp.weixin.qq.com/)->基本配置->服务器配置->令牌(Token) 
3. 拷贝此目录的配置文件 `config.json`，填写配置，放到你的服务器。
4. 使用Docker启动服务
  ```bash
  # 运行服务 (举例使用80端口，如果有域名会配置nginx自己修改别的端口号)
  docker run -d -p 80:80 -v $PWD/log:/app/log -v $PWD/config.json:/app/config.json tomatocuke/openai
  # 查看状况
  docker logs 容器ID 
  ```
1. 验证服务 `curl 'http://127.0.0.1/test?msg=怎么做锅包肉'` 
2. 公众号配置。 服务器地址(URL)填写 `http://服务器IP/wx`，设置明文方式传输，提交后，点击「启用」。 初次设置生效要等一会，过几分钟关闭再启用试试
    

### 三、其他
- 有什么问题我github可能不及时查看，欢迎提问和交流，QQ:`772532526`
