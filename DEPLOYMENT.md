# GaussHub 部署配置说明

## 环境配置文件

项目包含以下配置文件：

- `.env.example` - 配置模板文件（已提交到Git）
- `.env.local` - 本地开发环境配置（包含真实密钥，不提交Git）
- `.env.production` - 生产环境配置（包含真实密钥，不提交Git）

## 快速开始

### 1. 环境配置

```bash
# 复制配置模板
cp .env.example .env.local

# 编辑配置文件，填入真实的API密钥和配置
nano .env.local
```

### 2. 所需服务账号

#### AI服务
- **通义千问API**: [https://dashscope.aliyun.com/](https://dashscope.aliyun.com/)
- **Google Gemini API**: [https://ai.google.dev/](https://ai.google.dev/)

#### 邮件服务
- **Resend**: [https://resend.com/](https://resend.com/)

#### 企业集成
- **企业微信**: [https://work.weixin.qq.com/](https://work.weixin.qq.com/)
- **GitHub**: 个人访问令牌用于CI/CD集成

### 3. 基础设施要求

#### 服务器配置
- **CPU**: 4核心
- **内存**: 8GB RAM  
- **操作系统**: Ubuntu 22.04 LTS
- **存储**: 100GB+ SSD

#### 数据库
- **PostgreSQL**: 14+
- **Redis**: 6+
- **Elasticsearch**: 8+

#### 容器化
- **Docker**: 20+
- **Kubernetes**: 1.25+

### 4. 生产部署

#### 服务器信息
- **IP地址**: 103.251.89.105
- **SSH端口**: 4100
- **域名**: ai-sensor360.com

#### 部署步骤
1. 环境准备
2. 数据库初始化
3. 应用部署
4. 监控配置
5. 备份设置

## 安全注意事项

1. **永远不要将包含真实密钥的.env文件提交到Git**
2. **定期轮换API密钥和访问令牌**
3. **使用强密码和双因素认证**
4. **配置防火墙规则限制访问**
5. **启用SSL/TLS加密传输**

## 监控和日志

- 应用监控：Prometheus + Grafana
- 日志聚合：ELK Stack
- 错误追踪：Sentry
- 性能监控：New Relic

## 备份策略

- 数据库：每日自动备份
- 文件存储：实时同步备份
- 配置文件：版本控制管理
- 系统镜像：定期快照

## 故障排除

常见问题和解决方案请参考项目Wiki或联系技术支持团队。