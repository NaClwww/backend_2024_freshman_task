# HDU_BBS

## api 说明(未说明下默认为get)

"/" : 欢迎页，无需任何权限

### 用户相关

"register" : 注册页（post），需发送表单，分别为 username,password

"login" :登录页，同上，成功登录后会生成一个包含时间的cookie，cookie组成为uuid+日期，十天后过期，要求重新登录

"home" :返回用户个人信息（id，name），拥有cookie才能访问

"deleteuser":删除用户，仅admin可用，需提供id（user）

### 帖子相关

"addpost" : 增加帖子（post），需发送表单，分别为 title，text和father，father内容为fatherId，能供存储上一篇（或者回答的）帖子的id信息，同时会在father帖中的children项加入新帖的id

"viewpost" :需提供id，返回当前贴的id，title，text，time，belong，father和children

"deletepost":删除帖子，仅admin可用，需提供id（user），但不会消除children帖，需前端多次请求