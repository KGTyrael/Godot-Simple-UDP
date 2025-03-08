# SimpleUDP 插件 | SimpleUDP Plugin

这是一个简单的Godot UDP网络通信插件，提供基本的UDP通信功能。
This is a simple Godot UDP networking plugin that provides basic UDP communication functionality.

## 作者信息 | Author Information
- 作者 | Author: EBGame Studio - 摸摸鱼玩游戏
- 主页 | Homepage: https://space.bilibili.com/13651987
- 版本 | Version: 1.0.0
- Godot 兼容性 | Godot Compatibility: 4.x

## 功能特性 | Features

- UDP消息发送和接收 | UDP message sending and receiving
- UDP广播支持 | UDP broadcast support
- 自动管理的网络连接 | Auto-managed network connections
- 简单易用的API | Simple and easy-to-use API
- 包含完整示例 | Complete examples included

## 系统要求 | Requirements

- Godot 4.0 或更高版本 | Godot 4.0 or higher
- 无其他依赖 | No additional dependencies

## 安装方法 | Installation

1. 将`addons/simple_udp`目录复制到你的Godot项目的`addons`目录下
   Copy the `addons/simple_udp` directory to your Godot project's `addons` directory
2. 在Godot编辑器中，转到"项目 -> 项目设置 -> 插件"
   In Godot editor, go to "Project -> Project Settings -> Plugins"
3. 找到"SimpleUDP"插件并启用它
   Find the "SimpleUDP" plugin and enable it

## 使用方法 | Usage

### 基本用法 | Basic Usage

1. 在场景中添加一个节点 | Add a node to your scene
2. 将节点类型改为`UDPManager` | Change the node type to `UDPManager`
3. 连接`received`信号来处理接收到的消息 | Connect the `received` signal to handle incoming messages

```gdscript
# 创建UDPManager实例 | Create UDPManager instance
var udp = UDPManager.new()
add_child(udp)

# 启动UDP服务（指定端口） | Start UDP service (specify port)
udp.start(9000)

# 连接信号 | Connect signal
udp.received.connect(_on_message_received)

# 发送消息 | Send message
udp.send("Hello", "127.0.0.1", 9000)

# 广播消息 | Broadcast message
udp.broadcast("Hello everyone", 9000)

# 接收消息的回调函数 | Message received callback function
func _on_message_received(msg: String, ip: String, port: int) -> void:
	print("收到来自 | Received from %s:%d: %s" % [ip, port, msg])
```

### 示例场景 | Example Scene

插件包含了一个完整的示例场景，展示了如何使用所有功能。你可以在`addons/simple_udp/example`目录下找到`UDPExample.tscn`。
The plugin includes a complete example scene demonstrating all features. You can find `UDPExample.tscn` in the `addons/simple_udp/example` directory.

## API参考 | API Reference

### 信号 | Signals

- `received(msg: String, ip: String, port: int)` - 当收到UDP消息时触发 | Emitted when a UDP message is received

### 方法 | Methods

- `start(listen_port: int)` - 启动UDP服务并绑定到指定端口 | Start UDP service and bind to specified port
- `send(text: String, ip: String, port: int) -> Error` - 发送UDP消息到指定IP和端口 | Send UDP message to specified IP and port
- `broadcast(text: String, bcast_port: int) -> Error` - 广播UDP消息到指定端口 | Broadcast UDP message to specified port
- `close()` - 关闭UDP服务 | Close UDP service

## 更新日志 | Changelog

### 1.0.0
- 初始版本 | Initial release
- 基本的UDP通信功能 | Basic UDP communication features
- 完整的示例场景 | Complete example scene

## 许可证 | License

本项目采用 MIT 许可证。查看 [LICENSE](LICENSE) 文件了解更多信息。
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## 贡献 | Contributing

欢迎提交问题报告和改进建议！
Issues and pull requests are welcome!
