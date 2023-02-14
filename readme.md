# ChatGPT在线

AIChatAPI 是一个简单的API，它使用OpenAI的GPT-3 API来生成对消息的响应。

## 如何运行

1. 安装依赖

   ```
   pip install -r requirements.txt
   ```

2. 设置环境变量

   ```
   export API_KEY=<Your OpenAI API Key>
   export PASSWORD=<Your Password>
   ```

3. 启动应用

   ```
   python main.py
   ```

4. 在浏览器中打开 http://localhost:80/

## API文档

### `PUT /`

更新API密钥。

#### 参数

- `pwd` (str) - 访问密码，可以在启动日志中查看。
- `token` (str) - 新的API密钥。

#### 响应

- `code` (int) - 状态码，200 表示成功，403 表示密码错误。
- `msg` (str) - 响应消息。

### `POST /`

生成AI回复。

#### 参数

- `msg` (str) - 用户的消息。
- `history` (List[List[str]]) - 对话历史。
- `prompt` (str) - GPT-3的prompt文本。
- `token` (str) - API密钥。

#### 响应

- `code` (int) - 状态码，200 表示成功，500 表示API密钥无效或过期。
- `msg` (str) - 响应消息，`success` 表示成功，`回复过长，已被截断，如需更长的回复，请购买API_KEY` 表示回复超过了免费额度。
- `data` (List[str]) - 包含用户的消息和AI的回复。
- 
## Docker一键部署
### AMD
```shell
docker run -d --restart=always -p 80:80 --name aichat lanol/aichat:latest
```
### ARM
```shell
docker run -d --restart=always -p 80:80 --name aichat lanol/aichat:arm
```