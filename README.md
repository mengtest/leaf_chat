# leaf_chat
## leaf引擎的分布式聊天室范例
1. 此架构比较适合大厅类+房间式的游戏，其它游戏类型也可以通过修改调整完成；<br>
2. 此架构是建立在我自己的leaf分支上，请下载https://github.com/heyilin416/leaf ；<br> 
3. 此架构分成4类服务器：<br>
>- worldServer:世界服，负责服务器的管理，包括服务器的动态加载、负载均衡等中心功能；<br>
>- loginServer:登录服，负责帐号的信息管理与验证功能，此服为无状态服，可以通过nginx来均衡负载，可以横向扩展；<br> 
>- chatServer:聊天服，也是所谓的房间服，主要负责房间内游戏相关逻辑处理，此服可以横向扩展，分配由worldServer负责；<br>
>- frontServer:前端服，也是所谓的大厅服，玩家在与房间逻辑无关的时候，玩家的数据处理等各种功能由此服负责，此服可以横向扩展，分配由worldServer负责；<br>
>- chatClient:这是用go写的配套客户端，只能用命令行来操作，启动之后，可以通过打help来获取相关命令帮助。<br>
		
## 启动要求
chatServer和frontServer是支持横向扩展，所以启动的时候要传入配置文件名称，chatServer1.json和frontServer1.json，你可以通过加其它配置文件，来增加这两种服务器实例；
