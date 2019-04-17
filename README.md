# WebServer
## Java入门：学习做一个服务端，处理客户端请求
新建一个Maven项目WebServer  
### 1 WebServer
用于调试时启动服务端的主类。

### 2 ClientHandler
用于处理客户端请求

### 3 HttpRequest
请求对象  
该类的每一个实例用于表示浏览器发送过来的一个请求内容，每个请求由三部分构成(请求行，消息头，消息正文);
```
/**
	 * 通过对应客户端的输入流读取一行字符串(以CRLF结尾)
	 * 
	 * @return
	 * @throws IOException
	 */
	private String readLine() throws IOException {
		// 读取一行字符串，以CRLF结尾
		StringBuilder builder = new StringBuilder();
		// c1表示上次读取到的字符，c2表示本次读取到的字符
		int c1 = -1, c2 = -1;
		while ((c2 = in.read()) != -1) {
			// 是否连续读取到了CR，LF
			if (c1 == 13 && c2 == 10) {
				break;
			}
			builder.append((char) c2);
			c1 = c2;
		}
		return builder.toString().trim();
	}
```

### 4 HttpResponse
响应对象  
该类的每个实例用于表示发送给客户端的响应内容；  
一个响应包含三部分:状态行，响应头，响应正文。

### 5 EmptyRequestException
空请求异常

### 6 HttpContext
HTTP协议规定的相关内容
