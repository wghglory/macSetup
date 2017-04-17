# windows Dev setup

1. IIS

   > 先装 IIS 话，后面装 Net Framework 时候会自动注册、处理 aspx 和 ashx 等的处理扩展程序先装 Net Framework 后装 IIS。扩展程序注册在命令：`aspnet_regiis -i` 两个地方：
   >
   > - 第一步：开启 cmd 命令窗口（用管理员账户打开）C:\Windows\System32\cmd.exe
   > - 第二步：定位到目录：cd C:\Windows\Microsoft.NET\Framework\v4.0.30319
   > - 第三步：在 Vs 的命令提示符程序中注册一下：`aspnet_regiis -i`

1. sql: HeidiSql, Mongodb, MongoVUE, MySqlWorkBench(mac), sql server 2016, sqliteStudio

1. vs 2017: reSharper, developer assistant, spring.net, productivity power tools, web Essentials (zenCoding/emmet), sideWaffle

1. atom、vscode

1. nodejs

1. [mongodb](http://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows/)

   a) Set up the MongoDB environment. MongoDB requires a data directory to store all data. MongoDB’s default data directory path is `\data\db`. Create this folder using the following commands from a Command Prompt:

   ```bash
   cd c:\
   md \data\db
   ```

   b) You can specify an alternate path for data files using the `--dbpath` option to mongod.exe, for example:

   ```bash
   C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe --dbpath c:\mongodb\data
   C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe --config "C:\mongodb\mongod.cfg" --install
   ```

   c) mongostart.bat:

   ```bash
   cd C:\Program Files\MongoDB\Server\3.0\bin\
   mongod.exe --dbpath c:\mongodb\data
   ```

1. Dash
1. VLC
1. 好压
1. foxit
1. office(onenote)
1. 酷狗音乐
1. sougou input, explorer
