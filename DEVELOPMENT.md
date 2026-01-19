# Auto-Math-Grader 开发文档

## 项目概述

Auto-Math-Grader 是一个高等数学自动批改系统，通过大模型技术实现学生作业的自动识别、理解和评分。

### 核心功能

- 学生作业图片识别
- 数学题目理解与推理
- 自动评分与反馈
- 用户管理（待开发）
- 作业管理系统（待开发）

## 技术栈

### 后端服务
- **语言**: Golang 1.20
- **框架**: 待定
- **职责**: 业务逻辑、API服务、数据处理

### AI服务
- **语言**: Python 3.10
- **框架**: 待定
- **职责**: 大模型API调用、图片识别、推理计算

### 数据存储（待开发）
- **关系型数据库**: MySQL
- **缓存**: Redis

## 开发环境要求

### 服务器环境
- **操作系统**: Ubuntu 22.04 LTS
- **Go版本**: 1.20
- **Python版本**: 3.10

### 必需软件
```bash
# Go环境
go version  # 应显示 go1.20.x

# Python环境
python3 --version  # 应显示 Python 3.10.x
pip3 --version

# 数据库（后续开发）
mysql --version
redis-server --version
```

## 项目架构

```
auto-math-grader/
├── backend/              # Go后端服务
│   ├── api/             # API路由和处理器
│   ├── service/         # 业务逻辑层
│   ├── model/           # 数据模型
│   └── main.go          # 入口文件
├── ai-service/          # Python AI服务
│   ├── api_client/      # 大模型API客户端
│   ├── image_recognize/ # 图片识别模块
│   ├── math_reasoning/  # 数学推理模块
│   └── main.py          # 入口文件
├── frontend/            # 前端应用（待开发）
└── docs/                # 文档
```

## 开发阶段规划

### 第一阶段：后端逻辑开发（当前）
- [ ] Go后端基础框架搭建
- [ ] API路由设计
- [ ] 业务逻辑层实现
- [ ] 数据模型定义
- [ ] 与Python AI服务的通信接口

### 第二阶段：AI服务开发
- [ ] Python服务框架搭建
- [ ] DeepSeek API集成
- [ ] 图片识别API集成
- [ ] 数学推理逻辑实现
- [ ] 错误处理和重试机制

### 第三阶段：数据库集成（待开发）
- [ ] MySQL数据库设计
- [ ] Redis缓存集成
- [ ] ORM框架选择与配置
- [ ] 数据迁移脚本

### 第四阶段：前端开发（待开发）
- [ ] 用户注册/登录
- [ ] 作业上传界面
- [ ] 评分结果展示
- [ ] 用户管理后台

## API设计

### 大模型API集成

#### DeepSeek API（推理）
- **用途**: 数学题目理解和推理
- **调用方式**: OpenAI通用调用方法
- **API端点**: 待配置
- **认证方式**: API Key

#### 图片识别API（待选择）
- **用途**: 学生作业图片识别
- **功能**: OCR文字识别、公式识别
- **候选方案**:
  - GPT-4 Vision
  - 百度OCR
  - 腾讯云OCR
  - 其他专业数学公式识别API

### 服务间通信
- **协议**: HTTP/REST 或 gRPC
- **数据格式**: JSON
- **认证**: JWT或API Key

## 开发规范

### Go代码规范
- 遵循 Go 官方代码风格指南
- 使用 gofmt 格式化代码
- 使用 go vet 进行静态检查
- 编写单元测试

### Python代码规范
- 遵循 PEP 8 编码规范
- 使用 black 或 autopep8 格式化代码
- 使用 pylint 或 flake8 进行代码检查
- 编写单元测试

### Git提交规范
```
<type>(<scope>): <subject>

<body>

<footer>
```

Type类型：
- feat: 新功能
- fix: 修复bug
- docs: 文档更新
- style: 代码格式调整
- refactor: 重构
- test: 测试相关
- chore: 构建/工具相关

## 配置管理

### 环境变量
```bash
# Go服务
GO_ENV=development
GO_PORT=8080

# Python AI服务
PYTHON_ENV=development
PYTHON_PORT=5000

# API密钥
DEEPSEEK_API_KEY=your_api_key_here
IMAGE_RECOGNITION_API_KEY=your_api_key_here

# 数据库（后续）
MYSQL_HOST=localhost
MYSQL_PORT=3306
MYSQL_USER=root
MYSQL_PASSWORD=password
MYSQL_DATABASE=auto_math_grader

REDIS_HOST=localhost
REDIS_PORT=6379
```

## 部署说明

### 开发环境启动
```bash
# 启动Go后端
cd backend
go run main.go

# 启动Python AI服务
cd ai-service
python3 main.py
```

### 生产环境部署（待完善）
- 使用 Docker 容器化部署
- Nginx 反向代理
- Systemd 服务管理
- 日志收集与监控

## 测试计划

### 单元测试
- Go后端业务逻辑测试
- Python AI服务模块测试

### 集成测试
- 服务间通信测试
- API端到端测试

### 性能测试
- 并发请求处理能力
- 大模型API调用响应时间

## 注意事项

1. **API密钥安全**: 所有API密钥必须通过环境变量配置，不得硬编码在代码中
2. **错误处理**: 完善的错误处理和日志记录机制
3. **限流控制**: 大模型API调用需要实现限流和重试机制
4. **数据验证**: 对用户输入进行严格验证
5. **性能优化**: 考虑使用缓存、异步处理等优化手段

## 参考资料

- [Go官方文档](https://golang.org/doc/)
- [Python官方文档](https://docs.python.org/3.10/)
- [DeepSeek API文档](https://platform.deepseek.com/api-docs/)
- [OpenAI API文档](https://platform.openai.com/docs)

## 联系方式

项目维护者: Domoral
