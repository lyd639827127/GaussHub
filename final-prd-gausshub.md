# 产品需求文档 (PRD): GaussHub - 3D霍尔传感器市场赋能与情报平台

**项目名称**: GaussHub - 昆泰芯微3D霍尔传感器市场赋能与情报平台  
**文档版本**: V1.0 Final (最终整合版)  
**创建日期**: 2025年8月31日  
**项目负责人**: [项目负责人]  
**技术负责人**: [技术负责人]  
**文档状态**: 最终版 - 可执行

---

## 目录

1. [项目概述与背景](#1-项目概述与背景)
2. [市场需求分析](#2-市场需求分析)  
3. [用户角色与场景](#3-用户角色与场景)
4. [产品功能规划](#4-产品功能规划)
5. [技术架构设计](#5-技术架构设计)
6. [数据模型定义](#6-数据模型定义)
7. [AI增强功能](#7-AI增强功能)
8. [开发环境配置](#8-开发环境配置)
9. [集成接口规范](#9-集成接口规范)
10. [测试验收标准](#10-测试验收标准)
11. [实施计划与里程碑](#11-实施计划与里程碑)
12. [风险管理与应对](#12-风险管理与应对)
13. [附录：配置信息与测试数据](#13-附录配置信息与测试数据)

---

## 1. 项目概述与背景

### 1.1 项目愿景

GaussHub是昆泰芯微专为3D霍尔传感器业务打造的一体化数字平台，通过构建"**知识沉淀→快速赋能→数据洞察**"的完整闭环，解决技术销售过程中的核心痛点，最终实现Design-in项目的显著增长和客户满意度的全面提升。

### 1.2 核心问题定义

**业务痛点**：
- **方案复用率低**：典型应用与磁路配置分散在个人经验中，重复答疑严重
- **响应链条长**：客户问题→销售→FAE→应用→研发的多跳传递导致响应延迟
- **数据不可用**：Design-in定义不统一、阶段无口径、统计不可复现
- **情报滞后**：竞品参数、价格与案例零散，缺少结构化更新机制

**技术痛点**：
- 磁路设计know-how在传递给一线时出现衰减
- FAE面对位置精度、抗杂散磁场、多轴串扰等技术问题支持效率不高
- 新兴应用需求未能系统性收集分析，影响下一代产品规划

### 1.3 价值主张

以"**可复用的参考设计 + 可执行的检查清单 + 可闭环的工单→知识**"打通市场一线与中台知识沉淀，用数据化定义Design-in，缩短响应时间并提升首成率。

### 1.4 北极星指标

**主指标**: **月度活跃Design-in项目数（MA-DI）**  
- 定义：当月处于活跃阶段（Discovery/Engage/Sample/EVT/DVT/PVT/MP）且有有效活动记录的项目数

**驱动指标**:
- I1: 客户问题平均首响时长（小时）
- I2: 工单→知识转化率（%）与首发通过率（%）
- I3: 设计检查清单"完成并通过"次数/项目
- I4: 参考设计被复用次数（次/月）

---

## 2. 市场需求分析

### 2.1 目标市场机会

| 目标市场 | 市场规模(2025) | 增长率 | 当前份额 | 机会分析 |
|---------|--------------|--------|---------|----------|
| 汽车电子HMI | 15亿元 | 18% | 8% | 头部客户要求完整解决方案支持 |
| 工业控制 | 8亿元 | 12% | 15% | 需求稳定，重视技术服务 |
| 消费电子 | 12亿元 | 25% | 5% | 快速响应是赢得订单关键 |

### 2.2 应用场景分析

**汽车电子应用**：
- 换挡器、方向盘控制、踏板位置、座椅调节
- 关键需求：车规级认证、高可靠性、温度稳定性

**工业自动化**：
- 摇杆控制、阀门位置、机械手关节、电机位置反馈
- 关键需求：长期稳定性、抗干扰能力、精度要求

**消费电子**：
- 游戏手柄、鼠标滚轮、智能家电旋钮、VR设备
- 关键需求：低功耗、小尺寸、成本敏感

### 2.3 竞争态势分析

| 竞品 | 优势 | 劣势 | 我们的机会 |
|------|------|------|----------|
| AMS(艾迈斯) | 完整工具链 | 主要面向大客户 | 中小客户服务 |
| Infineon | 在线设计向导 | 本地化不足 | 本土化支持优势 |
| Melexis | 文档丰富 | 缺乏交互工具 | 数字化工具创新 |

---

## 3. 用户角色与场景

### 3.1 核心用户画像

#### 3.1.1 一线FAE (占使用量60%)
**典型工作流程**：
- 上午：客户现场调试（40%时间遇到重复性问题）
- 下午：整理技术方案（30%时间在找参考资料）
- 晚上：微信群里回复客户问题

**核心痛点**：
- P0: 客户现场无法快速验证磁路设计合理性（每周3-5次）
- P1: 找不到类似应用的参考设计（50%新项目）
- P1: 竞品对比数据散落各处，说服力不足

#### 3.1.2 销售经理 (占使用量20%)
**决策困境**：
- 团队无法清楚说明产品技术优势
- 缺少有说服力的成功案例材料
- 难以快速响应客户技术咨询

#### 3.1.3 产品管理团队 (占使用量15%)
**信息需求**：
- 无法量化评估功能需求的市场价值
- 客户反馈碎片化，难以形成产品洞察
- 缺乏竞品动态的系统性跟踪

### 3.2 高频使用场景

**S1 客户问题处理**：
```
客户提问 → 工单创建 → 同类案例/参考设计联想 → 建议配置与风险提示
```

**S2 现场技术支持**：
```
FAE现场调试 → "设计检查清单"勾选 → 导出PDF报告 → 回填工单/知识库
```

**S3 管理决策支持**：
```
周会看板 → Design-in活跃度 → 转化漏斗 → 响应时效 → 问题TopN
```

**S4 方案复用场景**：
```
按应用领域检索 → 磁路/固件参考配置 → 二次编辑 → 客户定制
```

---

## 4. 产品功能规划

### 4.1 MVP版本功能 (V1.0)

#### 4.1.1 工单管理系统
**核心流程**：创建→分派→处理→总结→转知识/关闭

**功能特性**：
- 智能推荐：创建工单时自动推荐相关知识库文章
- 字段管理：标题、客户/账号、应用域、产品系列、问题类型、严重度
- 状态追踪：完整的工单生命周期管理
- 协作功能：评论、@提醒、文件附件
- 一键转知识：将解决方案快速转化为知识库文章

#### 4.1.2 知识库管理
**强模板结构**：
- 问题现象、根因分析、实验条件与数据
- 修复/参数建议、适用范围与限制
- 失败模式（FMEA摘要）、脚本/参考代码
- 版本控制、标签分类、作者/评审信息

**质量控制**：
- 评审门槛：首发评审通过率≥80%
- 季度复审，过期标识与更新提醒
- 全文搜索，智能推荐

#### 4.1.3 设计检查清单
**应用域覆盖**：
- 摇杆、滚轮、踏板、方向盘/换挡、座椅、BLDC位置

**检查维度**：
- 磁路：磁材/充磁方式/尺寸/气隙/对准
- 传感器：轴向/饱和/灵敏度配置
- 硬件：供电/接口/滤波/ESD/EMC
- 固件：采样率/校准/诊断
- 环境：温度/振动/老化测试

**输出产物**：PDF报告（含签名、时间戳、项目编号）

#### 4.1.4 参考设计库
**设计卡片内容**：
- 应用域/目标指标/磁路配置
- 传感器与固件参数/原理图与PCB尺寸
- BOM清单/已知风险/适用范围
- 版本与时间戳

**复用功能**：
- 一键复制为项目草稿
- 关联项目与知识库
- 使用统计与热度排行

#### 4.1.5 基础数据看板
**关键指标卡片**：
- MA-DI、首响时长P50/P90、解决时长P50/P90
- 工单→知识转化率、检查清单通过次数
- 参考设计复用次数、TopN问题分析

**多维度分析**：
- 时间维度：日/周/月/季度趋势
- 空间维度：地区/客户分布
- 产品维度：应用域/产品系列

### 4.2 V2.0增强功能规划

#### 4.2.1 磁路设计助手
**参数化设计向导**：
- 应用场景选择（摇杆/旋钮/滑块等）
- 磁铁规格输入（材料/尺寸/充磁方向）
- 传感器选型自动推荐
- 安装位置建议

**设计规则校验**：
- 磁场强度检查（20-70mT范围）
- 线性度评估（误差<5%）
- 温度漂移预估
- EMC兼容性检查

#### 4.2.2 AI智能功能
**检索问答（RAG）**：
- 双语检索支持
- "CITE or FAIL"原则：必须提供来源
- 结构化字段自动抽取

**内容共创**：
- 工单→知识库文章自动转化
- 质量自检：格式/术语/敏感信息扫描
- 多版本对比与合并建议

**智能路由**：
- 新工单相似案例匹配
- 重复工单合并建议
- 风险识别与自动升级

#### 4.2.3 高级分析功能
**预测分析**：
- Design-in成功率预测
- 客户流失风险预警
- 产品缺陷模式识别

**竞品情报**：
- 自动化竞品信息收集
- 价格趋势分析
- 技术规格对比

---

## 5. 技术架构设计

### 5.1 系统架构概览

```
┌─────────────────────────────────────────────────────┐
│                    前端应用层                         │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐ │
│  │ Web端    │ │ 移动端H5  │ │ 企业微信  │ │ API    │ │
│  │ React 18 │ │ PWA      │ │ 小程序    │ │ Gateway│ │
│  └──────────┘ └──────────┘ └──────────┘ └────────┘ │
├─────────────────────────────────────────────────────┤
│                    业务服务层                         │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐ │
│  │知识管理  │ │工单系统   │ │设计工具   │ │AI引擎  │ │
│  │Node.js   │ │Node.js   │ │Python    │ │Python  │ │
│  └──────────┘ └──────────┘ └──────────┘ └────────┘ │
├─────────────────────────────────────────────────────┤
│                    基础服务层                         │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐ │
│  │用户认证  │ │权限管理   │ │消息通知   │ │文件存储│ │
│  │JWT+OAuth │ │RBAC      │ │WebSocket │ │MinIO   │ │
│  └──────────┘ └──────────┘ └──────────┘ └────────┘ │
├─────────────────────────────────────────────────────┤
│                    数据持久层                         │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐ │
│  │PostgreSQL│ │ Redis    │ │Elasticsearch│ │MinIO  │ │
│  │主数据库  │ │缓存队列   │ │全文搜索    │ │文件存储│ │
│  └──────────┘ └──────────┘ └──────────┘ └────────┘ │
└─────────────────────────────────────────────────────┘
```

### 5.2 技术选型说明

| 技术栈 | 选择 | 理由 |
|-------|------|------|
| 前端 | React 18 + TypeScript + Ant Design | 成熟生态，组件丰富，企业级UI |
| 后端 | Node.js (Express) + Python (FastAPI) | 业务逻辑 + AI数据分析 |
| 数据库 | PostgreSQL + Redis + Elasticsearch | 关系数据 + 缓存 + 搜索 |
| 部署 | Docker + Kubernetes | 容器化，易扩展 |
| 消息队列 | Redis Pub/Sub + Bull Queue | 轻量级，易部署 |
| 文件存储 | MinIO | 私有化，S3兼容 |
| 监控 | Prometheus + Grafana | 开源完整方案 |

### 5.3 部署架构

**生产环境**：
```yaml
# docker-compose.yml 示例
version: '3.8'
services:
  nginx:
    image: nginx:alpine
    ports: ["80:80", "443:443"]
    volumes: ["./nginx.conf:/etc/nginx/nginx.conf"]
    
  frontend:
    image: gausshub-frontend:latest
    environment:
      - API_URL=http://backend:3000
      
  backend:
    image: gausshub-backend:latest  
    ports: ["3000:3000"]
    environment:
      - DB_HOST=postgres
      - REDIS_HOST=redis
      - ES_HOST=elasticsearch
    depends_on: [postgres, redis, elasticsearch]
    
  ai-service:
    image: gausshub-ai:latest
    ports: ["8000:8000"]
    environment:
      - QWEN_API_KEY=${QWEN_API_KEY}
      - GEMINI_API_KEY=${GEMINI_API_KEY}
      
  postgres:
    image: postgres:15
    volumes: ["postgres_data:/var/lib/postgresql/data"]
    environment:
      - POSTGRES_DB=gausshub
      - POSTGRES_PASSWORD=${DB_PASSWORD}
      
  redis:
    image: redis:7-alpine
    volumes: ["redis_data:/data"]
    
  elasticsearch:
    image: elasticsearch:8.11.0
    environment:
      - discovery.type=single-node
      - xpack.security.enabled=false
    volumes: ["es_data:/usr/share/elasticsearch/data"]
    
  minio:
    image: minio/minio:latest
    ports: ["9000:9000", "9001:9001"]
    environment:
      - MINIO_ACCESS_KEY=${MINIO_ACCESS_KEY}
      - MINIO_SECRET_KEY=${MINIO_SECRET_KEY}
    volumes: ["minio_data:/data"]
    command: server /data --console-address ":9001"

volumes:
  postgres_data:
  redis_data:
  es_data:
  minio_data:
```

---

## 6. 数据模型定义

### 6.1 核心实体设计

#### 6.1.1 用户与权限
```sql
-- 用户表
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    name VARCHAR(100) NOT NULL,
    role ENUM('admin', 'manager', 'fae', 'sales', 'rd') NOT NULL,
    department VARCHAR(50),
    phone VARCHAR(20),
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 权限控制
CREATE TABLE permissions (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    resource VARCHAR(50) NOT NULL,
    action VARCHAR(50) NOT NULL,
    description TEXT
);

CREATE TABLE role_permissions (
    role VARCHAR(20) REFERENCES users(role),
    permission_id INTEGER REFERENCES permissions(id),
    PRIMARY KEY (role, permission_id)
);
```

#### 6.1.2 客户与项目
```sql
-- 客户账户
CREATE TABLE accounts (
    id SERIAL PRIMARY KEY,
    name VARCHAR(200) NOT NULL,
    industry VARCHAR(100),
    region ENUM('CN', 'EU', 'US', 'APAC', 'Other'),
    tier ENUM('Strategic', 'Key', 'Standard') DEFAULT 'Standard',
    contact_info JSONB,
    crm_id VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Design-in项目
CREATE TABLE projects (
    id SERIAL PRIMARY KEY,
    project_code VARCHAR(50) UNIQUE NOT NULL,
    name VARCHAR(200) NOT NULL,
    account_id INTEGER REFERENCES accounts(id),
    application_domain ENUM('Joystick', 'Mouse Wheel', 'Pedal', 'Steering', 'Shifter', 'Seat', 'BLDC Position', 'Other'),
    product_series ENUM('KTH55xx', 'KTH57xx', 'KTH579x', 'Other'),
    stage ENUM('Discovery', 'Engage', 'Sample', 'EVT', 'DVT', 'PVT', 'MP', 'Lost', 'On-hold'),
    stage_updated_at TIMESTAMP,
    risk_level ENUM('Low', 'Medium', 'High') DEFAULT 'Medium',
    owners JSONB, -- {"sales": "user_id", "fae": "user_id", "pm": "user_id"}
    estimated_volume INTEGER,
    target_price DECIMAL(10,4),
    crm_ref VARCHAR(100),
    created_by INTEGER REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 6.1.3 工单系统
```sql
-- 工单
CREATE TABLE tickets (
    id SERIAL PRIMARY KEY,
    ticket_code VARCHAR(50) UNIQUE NOT NULL,
    title VARCHAR(300) NOT NULL,
    description TEXT NOT NULL,
    type ENUM('Technical', 'Commercial', 'Quality', 'Other'),
    severity ENUM('S1-Critical', 'S2-High', 'S3-Medium', 'S4-Low'),
    status ENUM('New', 'Assigned', 'In Progress', 'Pending', 'Resolved', 'Closed', 'Reopened'),
    priority INTEGER DEFAULT 3,
    account_id INTEGER REFERENCES accounts(id),
    project_id INTEGER REFERENCES projects(id),
    product_series ENUM('KTH55xx', 'KTH57xx', 'KTH579x', 'Other'),
    application_domain ENUM('Joystick', 'Mouse Wheel', 'Pedal', 'Steering', 'Shifter', 'Seat', 'BLDC Position', 'Other'),
    created_by INTEGER REFERENCES users(id),
    assigned_to INTEGER REFERENCES users(id),
    resolved_by INTEGER REFERENCES users(id),
    first_response_at TIMESTAMP,
    resolved_at TIMESTAMP,
    closed_at TIMESTAMP,
    tags TEXT[], -- PostgreSQL数组类型
    attachments JSONB, -- [{"name": "file.pdf", "path": "/uploads/...", "size": 1024}]
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 工单评论
CREATE TABLE ticket_comments (
    id SERIAL PRIMARY KEY,
    ticket_id INTEGER REFERENCES tickets(id) ON DELETE CASCADE,
    user_id INTEGER REFERENCES users(id),
    content TEXT NOT NULL,
    is_internal BOOLEAN DEFAULT false,
    attachments JSONB,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 6.1.4 知识库
```sql
-- 知识文章
CREATE TABLE knowledge_articles (
    id SERIAL PRIMARY KEY,
    title VARCHAR(300) NOT NULL,
    content TEXT NOT NULL,
    summary TEXT,
    category VARCHAR(100),
    tags TEXT[],
    status ENUM('Draft', 'Review', 'Published', 'Archived'),
    version INTEGER DEFAULT 1,
    template_type ENUM('Problem-Solution', 'Reference-Design', 'FAQ', 'Tutorial'),
    
    -- 模板字段
    problem_description TEXT,
    root_cause_analysis TEXT,
    experiment_data TEXT,
    solution_steps TEXT,
    applicable_scope TEXT,
    failure_modes TEXT, -- FMEA摘要
    reference_code TEXT,
    
    -- 元数据
    view_count INTEGER DEFAULT 0,
    like_count INTEGER DEFAULT 0,
    quality_score DECIMAL(3,2),
    
    -- 关联信息
    source_ticket_id INTEGER REFERENCES tickets(id),
    related_projects INTEGER[],
    
    -- 审核信息
    author_id INTEGER REFERENCES users(id),
    reviewer_id INTEGER REFERENCES users(id),
    published_by INTEGER REFERENCES users(id),
    next_review_at DATE,
    
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    published_at TIMESTAMP
);

-- 文章版本历史
CREATE TABLE article_versions (
    id SERIAL PRIMARY KEY,
    article_id INTEGER REFERENCES knowledge_articles(id) ON DELETE CASCADE,
    version INTEGER NOT NULL,
    content TEXT NOT NULL,
    change_log TEXT,
    created_by INTEGER REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 6.1.5 参考设计库
```sql
-- 参考设计
CREATE TABLE reference_designs (
    id SERIAL PRIMARY KEY,
    name VARCHAR(200) NOT NULL,
    description TEXT,
    application_domain ENUM('Joystick', 'Mouse Wheel', 'Pedal', 'Steering', 'Shifter', 'Seat', 'BLDC Position', 'Other'),
    product_series ENUM('KTH55xx', 'KTH57xx', 'KTH579x', 'Other'),
    
    -- 技术规格
    target_specs JSONB, -- {"resolution": "16bit", "interface": "I2C", "range": "±30deg"}
    magnetic_config JSONB, -- {"magnet_type": "NdFeB", "magnetization": "Radial", "dimensions": "D8xH4mm"}
    sensor_params JSONB,
    firmware_config JSONB,
    
    -- 设计文件
    schematic_files JSONB, -- [{"name": "schematic.pdf", "path": "/uploads/..."}]
    pcb_files JSONB,
    bom_data JSONB,
    test_data JSONB,
    
    -- 使用统计
    reuse_count INTEGER DEFAULT 0,
    last_used_at TIMESTAMP,
    
    -- 风险与限制
    known_risks TEXT,
    applicable_scope TEXT,
    version VARCHAR(20) DEFAULT 'v1.0',
    
    created_by INTEGER REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 设计复用记录
CREATE TABLE design_reuse_logs (
    id SERIAL PRIMARY KEY,
    design_id INTEGER REFERENCES reference_designs(id),
    project_id INTEGER REFERENCES projects(id),
    user_id INTEGER REFERENCES users(id),
    reuse_type ENUM('Direct-Copy', 'Modified', 'Inspired'),
    modifications TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 6.2 设计检查清单
```sql
-- 检查清单模板
CREATE TABLE checklist_templates (
    id SERIAL PRIMARY KEY,
    name VARCHAR(200) NOT NULL,
    application_domain ENUM('Joystick', 'Mouse Wheel', 'Pedal', 'Steering', 'Shifter', 'Seat', 'BLDC Position', 'Other'),
    version VARCHAR(20) DEFAULT 'v1.0',
    checklist_items JSONB, -- 检查项目的结构化定义
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 检查清单执行记录
CREATE TABLE checklist_runs (
    id SERIAL PRIMARY KEY,
    template_id INTEGER REFERENCES checklist_templates(id),
    project_id INTEGER REFERENCES projects(id),
    executed_by INTEGER REFERENCES users(id),
    execution_date DATE,
    
    -- 执行结果
    results JSONB, -- 每个检查项的结果
    overall_passed BOOLEAN,
    score INTEGER, -- 0-100
    
    -- 报告
    report_path VARCHAR(500), -- PDF报告文件路径
    report_generated_at TIMESTAMP,
    
    -- 签名信息
    signature JSONB, -- {"engineer": "name", "date": "2025-01-01", "sign": "base64_image"}
    
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 6.3 事件与指标
```sql
-- 业务事件
CREATE TABLE business_events (
    id SERIAL PRIMARY KEY,
    event_type VARCHAR(100) NOT NULL, -- 'ticket_created', 'knowledge_published'等
    entity_type VARCHAR(50) NOT NULL, -- 'ticket', 'article', 'project'等  
    entity_id INTEGER NOT NULL,
    
    -- 事件属性
    user_id INTEGER REFERENCES users(id),
    account_id INTEGER REFERENCES accounts(id),
    project_id INTEGER REFERENCES projects(id),
    properties JSONB, -- 事件相关的额外属性
    
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 指标计算结果缓存
CREATE TABLE metrics_cache (
    id SERIAL PRIMARY KEY,
    metric_name VARCHAR(100) NOT NULL,
    time_period VARCHAR(50) NOT NULL, -- 'daily', 'weekly', 'monthly'
    period_start DATE NOT NULL,
    period_end DATE NOT NULL,
    dimensions JSONB, -- {"region": "CN", "product": "KTH57xx"}
    value DECIMAL(15,4),
    calculation_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    UNIQUE(metric_name, time_period, period_start, dimensions)
);
```

### 6.4 数据词典

**关键枚举值定义**：
```sql
-- 应用域
application_domain: 'Joystick' | 'Mouse Wheel' | 'Pedal' | 'Steering' | 'Shifter' | 'Seat' | 'BLDC Position' | 'Other'

-- 产品系列
product_series: 'KTH55xx' | 'KTH57xx' | 'KTH579x' | 'Other'

-- 问题类型
problem_type: '性能' | '精度' | '噪声' | '温飘' | '通信' | 'I2C' | 'SPI' | 'PWM' | 'ABZ' | 'ESD' | 'EMC' | '机械' | '磁路' | '固件' | '量产' | '其他'

-- 严重程度
severity: 'S1-Critical' | 'S2-High' | 'S3-Medium' | 'S4-Low'

-- 项目阶段
stage: 'Discovery' | 'Engage' | 'Sample' | 'EVT' | 'DVT' | 'PVT' | 'MP' | 'Lost' | 'On-hold'

-- 磁化方式
magnetization: 'Radial' | 'Axial' | 'Diametral'

-- 接口类型
interface: 'I2C' | 'SPI' | 'PWM' | 'ABZ' | 'SENT' | 'Analog'

-- 地区
region: 'CN' | 'EU' | 'US' | 'APAC' | 'Other'
```

---

## 7. AI增强功能

### 7.1 AI能力体系

#### 7.1.1 检索问答（RAG）
**功能特性**：
- 双语检索：中英文混合搜索
- 混合召回：BM25 + 向量 + 知识图谱
- "CITE or FAIL"原则：必须提供来源卡片
- 结构化抽取：自动识别产品系列/应用域/接口等字段

**技术实现**：
```python
def intelligent_search(query: str, filters: dict) -> SearchResults:
    """
    智能搜索实现
    """
    # 1. 查询理解和意图识别
    intent = classify_intent(query)  # "technical_support", "product_info", etc.
    
    # 2. 实体抽取
    entities = extract_entities(query)  # {"product": "KTH5701", "domain": "Joystick"}
    
    # 3. 混合检索
    bm25_results = bm25_search(query, filters)
    vector_results = vector_search(query, filters) 
    kg_results = knowledge_graph_search(entities)
    
    # 4. 重排和融合
    ranked_results = cross_encoder_rerank(query, 
                                         combine_results(bm25_results, vector_results, kg_results))
    
    # 5. 生成回答
    answer = generate_answer_with_citations(query, ranked_results)
    
    return SearchResults(
        answer=answer,
        sources=ranked_results,
        confidence=calculate_confidence(answer, ranked_results)
    )
```

#### 7.1.2 内容共创（Author Assist）
**核心功能**：
- 工单→知识自动转换：问题现象→根因→实验→对策→适用范围→FMEA摘要
- 质量自检：格式检查、术语验证、敏感信息扫描
- 多版本对比：智能识别内容差异，提供合并建议

**模板生成示例**：
```python
def generate_knowledge_from_ticket(ticket: Ticket) -> KnowledgeTemplate:
    """
    从工单自动生成知识库文章模板
    """
    template = {
        "title": f"[{ticket.product_series}] {ticket.title}",
        "problem_description": extract_problem_description(ticket.description),
        "root_cause_analysis": analyze_root_cause(ticket.comments, ticket.resolution),
        "experiment_data": extract_test_data(ticket.attachments),
        "solution_steps": generate_solution_steps(ticket.resolution),
        "applicable_scope": determine_scope(ticket.product_series, ticket.application_domain),
        "failure_modes": generate_fmea_summary(ticket.type, ticket.resolution),
        "tags": generate_tags(ticket.title, ticket.description),
        "source_ticket_id": ticket.id
    }
    
    # 质量检查
    quality_issues = quality_check(template)
    template["quality_issues"] = quality_issues
    
    return template
```

#### 7.1.3 智能路由与去重
**功能实现**：
- 相似工单识别：基于语义相似度的重复检测
- 智能分派：根据问题类型和专家领域自动分配
- 风险预警：根据问题严重程度和历史数据预测升级风险

#### 7.1.4 知识治理（Librarian）
**自动化功能**：
- 实体抽取：自动识别产品型号、应用域、技术参数
- 过期检测：基于时间和版本信息识别过期内容
- 冲突检测：识别参数设置和技术方案的矛盾
- 质量评估：基于阅读量、反馈、专家评分的综合质量评估

### 7.2 Agent编队架构

```python
class AgentOrchestrator:
    """
    Agent编队调度器
    """
    def __init__(self):
        self.agents = {
            "router": RouterAgent(),           # 前门对话路由
            "fae_assistant": FAEAgent(),       # FAE专用助手
            "librarian": LibrarianAgent(),     # 知识馆员
            "rule_checker": RuleCheckAgent(),  # 规则校验
            "metrics": MetricsAgent()          # 数据观测
        }
    
    async def process_request(self, request: UserRequest) -> AgentResponse:
        # 1. 意图识别和路由
        intent = await self.agents["router"].classify_intent(request)
        
        # 2. 分派给专门的Agent处理
        primary_agent = self.select_primary_agent(intent)
        response = await primary_agent.process(request)
        
        # 3. 质量检查和审核
        if response.affects_knowledge_base:
            validation = await self.agents["rule_checker"].validate(response)
            response = response.apply_validation(validation)
        
        # 4. 埋点和指标记录
        await self.agents["metrics"].record_interaction(request, response)
        
        return response
```

### 7.3 AI服务配置

基于配置信息中的API密钥，系统将集成以下AI服务：

**模型配置**：
```yaml
ai_services:
  primary_llm:
    provider: "qwen"
    api_key: "sk-a7179778042a416591db79a4daf2ffa4"
    model: "qwen-max"
    max_tokens: 4096
    temperature: 0.1
    
  backup_llm:
    provider: "gemini"  
    api_key: "AIzaSyDOV22QEIYPBkBkG7kqja0IS1vzNMn8NC8"
    model: "gemini-1.5-pro"
    max_tokens: 4096
    temperature: 0.1
    
  embedding:
    provider: "qwen"
    model: "text-embedding-v2"
    
  vector_db:
    provider: "elasticsearch"
    index: "gausshub_knowledge"
    dimensions: 1024
```

---

## 8. 开发环境配置

### 8.1 基础环境

**服务器信息**：
- IP地址: 103.251.89.105
- SSH端口: 4100  
- 操作系统: Ubuntu 22.04 LTS
- 配置: 4核8GB RAM
- 域名: ai-sensor360.com

**开发工具配置**：
```bash
# Docker镜像源配置
echo '{
  "registry-mirrors": ["https://ksveefkaa6do8z.xuanyuan.run"]
}' > /etc/docker/daemon.json

# Python包管理
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

# Node.js环境
nvm install 18
nvm use 18
npm config set registry https://registry.npmmirror.com
```

### 8.2 环境变量配置

```bash
# .env 文件
# 数据库配置
DB_HOST=postgres
DB_PORT=5432
DB_NAME=gausshub
DB_USER=postgres
DB_PASSWORD=your_secure_password

# Redis配置  
REDIS_HOST=redis
REDIS_PORT=6379
REDIS_PASSWORD=your_redis_password

# AI服务配置
QWEN_API_KEY=[Your Qwen API Key]
GEMINI_API_KEY=[Your Gemini API Key]

# 邮件服务
RESEND_API_KEY=[Your Resend API Key]

# 企业微信配置
WECHAT_CORP_ID=your_corp_id
WECHAT_AGENT_ID=1000003
WECHAT_SECRET=HtzF5dU7w9YDOUyxz-JILsVONpYtFotQQVrUsECyA3Q
WECHAT_TOKEN=nXhrG0THRecsLBeYRdrgn
WECHAT_AES_KEY=ch4moTyQhQgDdzuAyUaHzL3IdKY9s7GwkfvHMLGiQVv
WECHAT_CALLBACK_URL=http://ai-sensor360.com:3000/api/wechat/callback

# 文件存储
MINIO_ACCESS_KEY=gausshub_access
MINIO_SECRET_KEY=gausshub_secret_key
MINIO_ENDPOINT=minio:9000

# 应用配置
NODE_ENV=production
PORT=3000
JWT_SECRET=your_jwt_secret_key_here
API_BASE_URL=http://ai-sensor360.com:3000

# GitHub集成
GITHUB_TOKEN=[Your GitHub Personal Access Token]
```

### 8.3 开发工具链

**前端开发环境**：
```json
{
  "name": "gausshub-frontend",
  "version": "1.0.0",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "type-check": "tsc --noEmit"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "antd": "^5.12.0",
    "@ant-design/icons": "^5.2.6",
    "axios": "^1.6.0",
    "react-router-dom": "^6.20.0",
    "zustand": "^4.4.0",
    "dayjs": "^1.11.10"
  },
  "devDependencies": {
    "@types/react": "^18.2.0",
    "@types/react-dom": "^18.2.0",
    "@typescript-eslint/eslint-plugin": "^6.0.0",
    "@typescript-eslint/parser": "^6.0.0",
    "@vitejs/plugin-react": "^4.0.0",
    "eslint": "^8.45.0",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.0",
    "typescript": "^5.0.2",
    "vite": "^4.4.5"
  }
}
```

**后端开发环境**：
```json
{
  "name": "gausshub-backend",
  "version": "1.0.0",
  "scripts": {
    "dev": "nodemon --exec ts-node src/index.ts",
    "build": "tsc",
    "start": "node dist/index.js",
    "test": "jest",
    "lint": "eslint . --ext .ts",
    "type-check": "tsc --noEmit"
  },
  "dependencies": {
    "express": "^4.18.0",
    "pg": "^8.11.0",
    "redis": "^4.6.0",
    "@elastic/elasticsearch": "^8.11.0",
    "jsonwebtoken": "^9.0.0",
    "bcryptjs": "^2.4.3",
    "multer": "^1.4.5",
    "cors": "^2.8.5",
    "helmet": "^7.0.0",
    "winston": "^3.11.0",
    "joi": "^17.11.0",
    "axios": "^1.6.0"
  },
  "devDependencies": {
    "@types/express": "^4.17.0",
    "@types/node": "^20.8.0",
    "@types/pg": "^8.10.0",
    "@types/jsonwebtoken": "^9.0.0",
    "@types/bcryptjs": "^2.4.0",
    "@types/multer": "^1.4.0",
    "@types/cors": "^2.8.0",
    "@types/jest": "^29.5.0",
    "typescript": "^5.0.0",
    "ts-node": "^10.9.0",
    "nodemon": "^3.0.0",
    "jest": "^29.7.0",
    "ts-jest": "^29.1.0",
    "eslint": "^8.45.0",
    "@typescript-eslint/parser": "^6.0.0",
    "@typescript-eslint/eslint-plugin": "^6.0.0"
  }
}
```

---

## 9. 集成接口规范

### 9.1 企业微信集成

基于提供的企业微信配置信息，系统将实现完整的企业微信集成：

**配置信息**：
- AgentId: 1000003
- Secret: HtzF5dU7w9YDOUyxz-JILsVONpYtFotQQVrUsECyA3Q
- 回调URL: http://ai-sensor360.com:3000/api/wechat/callback
- Token: nXhrG0THRecsLBeYRdrgn
- EncodingAESKey: ch4moTyQhQgDdzuAyUaHzL3IdKY9s7GwkfvHMLGiQVv

**功能实现**：
```typescript
// 企业微信消息推送
class WeChatService {
    private corpId: string;
    private agentId: string;
    private secret: string;
    
    async sendTicketNotification(ticket: Ticket, users: string[]): Promise<void> {
        const accessToken = await this.getAccessToken();
        
        const message = {
            touser: users.join('|'),
            msgtype: 'textcard',
            agentid: this.agentId,
            textcard: {
                title: `新工单：${ticket.title}`,
                description: `客户：${ticket.account_name}\n产品：${ticket.product_series}\n严重程度：${ticket.severity}`,
                url: `http://ai-sensor360.com/tickets/${ticket.id}`,
                btntxt: '查看详情'
            }
        };
        
        await axios.post(`https://qyapi.weixin.qq.com/cgi-bin/message/send?access_token=${accessToken}`, message);
    }
    
    async handleCallback(req: Request): Promise<any> {
        // 处理企业微信回调消息
        const { msg_signature, timestamp, nonce } = req.query;
        const body = req.body;
        
        // 验证签名
        if (!this.verifySignature(msg_signature, timestamp, nonce, body)) {
            throw new Error('Invalid signature');
        }
        
        // 解密消息
        const decryptedMsg = this.decrypt(body);
        
        // 处理不同类型的消息
        switch (decryptedMsg.MsgType) {
            case 'text':
                return await this.handleTextMessage(decryptedMsg);
            case 'event':
                return await this.handleEventMessage(decryptedMsg);
            default:
                return { success: true };
        }
    }
}
```

### 9.2 RESTful API规范

**统一响应格式**：
```typescript
interface ApiResponse<T = any> {
    success: boolean;
    code: number;
    message: string;
    data?: T;
    meta?: {
        pagination?: PaginationMeta;
        timestamp: string;
        requestId: string;
    };
}

interface PaginationMeta {
    page: number;
    size: number;
    total: number;
    totalPages: number;
    hasNext: boolean;
    hasPrev: boolean;
}
```

**核心API端点**：

```yaml
# 用户认证
POST   /api/auth/login           # 用户登录
POST   /api/auth/logout          # 用户登出
POST   /api/auth/refresh         # 刷新Token
GET    /api/auth/profile         # 获取用户信息

# 工单管理
GET    /api/tickets              # 获取工单列表
POST   /api/tickets              # 创建新工单
GET    /api/tickets/:id          # 获取工单详情
PUT    /api/tickets/:id          # 更新工单
DELETE /api/tickets/:id          # 删除工单
POST   /api/tickets/:id/comments # 添加工单评论
POST   /api/tickets/:id/convert  # 转换为知识库文章

# 知识库管理
GET    /api/knowledge            # 获取知识库文章列表
POST   /api/knowledge            # 创建知识库文章
GET    /api/knowledge/:id        # 获取文章详情
PUT    /api/knowledge/:id        # 更新文章
DELETE /api/knowledge/:id        # 删除文章
POST   /api/knowledge/search     # 知识库搜索

# 参考设计
GET    /api/designs              # 获取参考设计列表
POST   /api/designs              # 创建参考设计
GET    /api/designs/:id          # 获取设计详情
POST   /api/designs/:id/reuse    # 记录设计复用

# 检查清单
GET    /api/checklists/templates # 获取检查清单模板
POST   /api/checklists/run       # 执行检查清单
GET    /api/checklists/runs/:id  # 获取执行结果
POST   /api/checklists/export    # 导出PDF报告

# 数据分析
GET    /api/analytics/dashboard  # 获取仪表盘数据
GET    /api/analytics/metrics    # 获取指标数据
GET    /api/analytics/reports    # 获取分析报告

# 文件管理
POST   /api/files/upload         # 文件上传
GET    /api/files/:id            # 文件下载
DELETE /api/files/:id            # 删除文件
```

### 9.3 Webhook机制

**事件通知**：
```typescript
interface WebhookEvent {
    event: string;
    timestamp: string;
    data: any;
    signature: string;
}

// 支持的事件类型
const WEBHOOK_EVENTS = [
    'ticket.created',
    'ticket.updated', 
    'ticket.resolved',
    'ticket.closed',
    'knowledge.published',
    'knowledge.updated',
    'project.stage_changed',
    'design.reused',
    'checklist.completed'
];

// 企业微信Webhook配置
const webhookConfig = {
    url: 'http://ai-sensor360.com:3000/api/wechat/callback',
    events: WEBHOOK_EVENTS,
    secret: 'nXhrG0THRecsLBeYRdrgn',
    retryPolicy: {
        maxRetries: 3,
        backoffMultiplier: 2,
        maxBackoffTime: 300000 // 5分钟
    }
};
```

---

## 10. 测试验收标准

### 10.1 功能测试标准

#### 10.1.1 MVP功能验收标准

| 功能模块 | 验收要点 | 验收方法 | 通过标准 |
|---------|---------|----------|----------|
| 用户系统 | 登录认证、权限控制、用户管理 | 功能测试用例执行 | 100%用例通过 |
| 工单系统 | 创建、分派、处理、转知识全流程 | 端到端测试 | 完整闭环无阻塞 |
| 知识库 | 文章创建、编辑、搜索、版本管理 | 功能测试+性能测试 | 功能完整+搜索<2s |
| 智能推荐 | 创建工单时推荐相关文章 | 准确率测试 | 推荐准确率>70% |
| 检查清单 | 5个应用域清单+PDF导出 | 实际案例验证 | 5个域覆盖+PDF正常生成 |
| 参考设计库 | 设计复用和统计追踪 | 功能测试 | 复用功能正常+统计准确 |
| 基础看板 | MA-DI等5项核心指标展示 | 数据一致性验证 | 指标计算准确+实时更新 |
| 企业微信集成 | 消息推送和回调处理 | 集成测试 | 消息正常收发 |

#### 10.1.2 详细测试用例

**工单系统测试用例**：
```gherkin
Feature: 工单智能推荐
  作为一个FAE用户
  我希望在创建工单时获得相似问题推荐
  以便快速找到解决方案

  Scenario: 创建工单时获得智能推荐
    Given 我是已登录的FAE用户
    When 我输入工单标题 "KTH5701传感器输出异常抖动"
    And 我选择产品系列 "KTH57xx"
    And 我选择应用域 "Joystick"
    Then 系统应该推荐至少3个相关的知识库文章
    And 推荐结果应该按相关性排序
    And 每个推荐应该显示标题和摘要
    And 我可以点击查看详情

  Scenario: 工单转知识库文章
    Given 我有一个已解决的工单
    When 我点击"转为知识库文章"
    Then 系统应该自动填入问题现象和解决方案
    And 生成的文章应该包含必要的模板字段
    And 文章状态应该为"草稿"
    And 我可以继续编辑完善内容
```

**知识库搜索测试用例**：
```gherkin
Feature: 知识库智能搜索
  作为用户
  我希望能够快速搜索到相关的技术文档
  以便解决遇到的问题

  Scenario: 关键词搜索
    Given 知识库中有相关的技术文档
    When 我搜索 "摇杆 线性度 校准"
    Then 搜索结果应该在2秒内返回
    And 结果应该按相关性排序
    And 应该高亮显示匹配的关键词
    And 应该显示文章的标签和分类

  Scenario: 筛选搜索
    Given 我在知识库搜索页面
    When 我搜索 "温度漂移"
    And 我选择产品系列筛选 "KTH57xx"
    And 我选择应用域筛选 "Joystick"
    Then 搜索结果应该只包含符合筛选条件的文章
    And 筛选器应该显示每个选项的文章数量
```

### 10.2 性能测试标准

**负载测试要求**：
```yaml
performance_requirements:
  response_time:
    api_calls: "< 200ms (P95)"
    page_load: "< 2s (first screen)"
    search: "< 500ms"
    file_upload: "< 5s for 10MB file"
    
  throughput:
    concurrent_users: "> 200"
    api_qps: "> 1000/s"
    search_qps: "> 100/s"
    
  availability:
    uptime: "> 99.9%"
    recovery_time: "< 5min"
    
  resource_usage:
    cpu_utilization: "< 70% under normal load"
    memory_usage: "< 80% of available RAM"
    disk_io: "< 70% of disk bandwidth"
```

**性能测试脚本示例**：
```javascript
// 使用K6进行负载测试
import http from 'k6/http';
import { check, sleep } from 'k6';

export let options = {
    stages: [
        { duration: '2m', target: 50 },   // 2分钟内增加到50用户
        { duration: '5m', target: 50 },   // 保持50用户5分钟
        { duration: '2m', target: 200 },  // 2分钟内增加到200用户
        { duration: '10m', target: 200 }, // 保持200用户10分钟
        { duration: '2m', target: 0 },    // 2分钟内降到0
    ],
    thresholds: {
        http_req_duration: ['p(95)<200'],  // 95%请求响应时间<200ms
        http_req_failed: ['rate<0.01'],    // 错误率<1%
    },
};

export default function() {
    // 登录
    let loginRes = http.post('http://ai-sensor360.com:3000/api/auth/login', {
        username: 'test_user',
        password: 'test_password'
    });
    
    check(loginRes, {
        'login successful': (r) => r.status === 200,
        'login response time OK': (r) => r.timings.duration < 500,
    });
    
    let token = loginRes.json('data.token');
    let headers = { 'Authorization': `Bearer ${token}` };
    
    // 获取工单列表
    let ticketsRes = http.get('http://ai-sensor360.com:3000/api/tickets', { headers });
    check(ticketsRes, {
        'tickets list loaded': (r) => r.status === 200,
        'tickets response time OK': (r) => r.timings.duration < 200,
    });
    
    // 搜索知识库
    let searchRes = http.post('http://ai-sensor360.com:3000/api/knowledge/search', 
        JSON.stringify({ q: '摇杆校准', filters: {} }),
        { headers: { ...headers, 'Content-Type': 'application/json' } }
    );
    
    check(searchRes, {
        'search successful': (r) => r.status === 200,
        'search response time OK': (r) => r.timings.duration < 500,
    });
    
    sleep(1);
}
```

### 10.3 安全测试标准

**安全测试要求**：
```yaml
security_requirements:
  authentication:
    - JWT token验证
    - 密码复杂度要求
    - 会话超时控制
    - 多次登录失败锁定
    
  authorization:
    - 基于角色的权限控制(RBAC)
    - API端点权限验证
    - 数据级权限控制
    - 跨租户数据隔离
    
  data_protection:
    - 敏感数据加密存储
    - 传输层TLS加密
    - 文件上传类型限制
    - SQL注入防护
    
  audit_logging:
    - 用户操作日志记录
    - 敏感操作审计跟踪
    - 日志完整性保护
    - 日志保留策略
```

**安全测试用例**：
```yaml
security_test_cases:
  - name: "SQL注入测试"
    type: "injection"
    target: "/api/tickets?search='; DROP TABLE tickets; --"
    expected: "返回400错误，不执行恶意SQL"
    
  - name: "XSS攻击测试"
    type: "xss"
    target: "/api/knowledge"
    payload: "<script>alert('xss')</script>"
    expected: "脚本被过滤或转义"
    
  - name: "未授权访问测试"
    type: "authorization"
    target: "/api/admin/users"
    headers: "无Authorization header"
    expected: "返回401未授权错误"
    
  - name: "CSRF攻击测试"
    type: "csrf"
    target: "/api/tickets"
    method: "POST"
    expected: "CSRF token验证失败，请求被拒绝"
```

### 10.4 集成测试标准

**企业微信集成测试**：
```typescript
describe('企业微信集成测试', () => {
    test('工单创建时发送微信通知', async () => {
        // 创建测试工单
        const ticket = await createTestTicket({
            title: 'KTH5701传感器异常',
            severity: 'S2-High',
            assigned_to: 'test_fae_user'
        });
        
        // 验证微信消息是否发送
        expect(mockWeChatAPI.sendMessage).toHaveBeenCalledWith(
            expect.objectContaining({
                touser: 'test_fae_user',
                msgtype: 'textcard',
                textcard: expect.objectContaining({
                    title: expect.stringContaining('KTH5701传感器异常'),
                    url: expect.stringContaining(`/tickets/${ticket.id}`)
                })
            })
        );
    });
    
    test('微信回调消息处理', async () => {
        const callbackPayload = {
            ToUserName: 'test_corp',
            FromUserName: 'test_user',
            CreateTime: Date.now(),
            MsgType: 'text',
            Content: '/ticket list',
            AgentID: 1000003
        };
        
        const response = await request(app)
            .post('/api/wechat/callback')
            .send(callbackPayload)
            .expect(200);
            
        expect(response.body).toEqual(
            expect.objectContaining({
                MsgType: 'text',
                Content: expect.stringContaining('您的工单列表')
            })
        );
    });
});
```

---

## 11. 实施计划与里程碑

### 11.1 项目实施时间线

```mermaid
gantt
    title GaussHub项目实施甘特图
    dateFormat YYYY-MM-DD
    section 准备阶段
    需求确认与设计      :a1, 2025-09-01, 10d
    环境搭建          :a2, 2025-09-01, 7d
    团队组建与培训      :a3, after a2, 5d
    
    section MVP开发 (V1.0)
    用户系统开发        :b1, after a1, 10d
    工单系统开发        :b2, after b1, 14d
    知识库系统开发      :b3, after b1, 14d
    参考设计库开发      :b4, after b2, 7d
    检查清单功能        :b5, after b3, 7d
    基础看板开发        :b6, after b4, 10d
    企业微信集成        :b7, after b5, 5d
    
    section 测试部署
    集成测试           :c1, after b6, 7d
    性能测试           :c2, after c1, 3d
    安全测试           :c3, after c1, 3d
    UAT测试           :c4, after c2, 5d
    问题修复           :c5, after c4, 7d
    生产部署           :c6, after c5, 3d
    
    section 推广培训
    培训材料准备        :d1, after c6, 5d
    用户培训           :d2, after d1, 3d
    试点上线           :d3, after d2, 7d
    全面推广           :milestone, after d3, 1d
    
    section V2.0开发
    AI功能开发         :e1, after d3, 21d
    高级分析功能        :e2, after e1, 14d
    磁路设计工具        :e3, after e2, 21d
    V2.0上线          :milestone, after e3, 1d
```

### 11.2 关键里程碑

| 里程碑 | 时间节点 | 交付物 | 验收标准 |
|--------|---------|--------|----------|
| M1: 项目启动 | 2025-09-15 | 项目计划、团队组建、环境搭建 | 开发环境可用，团队到位 |
| M2: MVP功能完成 | 2025-11-15 | 完整的V1.0系统 | 所有MVP功能通过测试 |
| M3: 生产部署 | 2025-11-30 | 生产环境系统 | 系统稳定运行，性能达标 |
| M4: 用户培训完成 | 2025-12-15 | 培训材料、用户反馈 | 80%目标用户完成培训 |
| M5: 全面推广 | 2025-12-31 | 推广方案执行 | 月活跃用户>70% |
| M6: V2.0发布 | 2026-03-31 | V2.0完整系统 | AI功能正常，用户满意度>85% |

### 11.3 资源需求规划

#### 11.3.1 人力资源需求

| 角色 | MVP阶段 | V2.0阶段 | 主要职责 |
|------|---------|----------|----------|
| 项目经理 | 1人(100%) | 1人(50%) | 项目管理、进度协调、风险控制 |
| 产品经理 | 1人(100%) | 1人(80%) | 需求分析、产品设计、用户反馈 |
| 前端开发 | 2人(100%) | 2人(100%) | React应用开发、UI组件实现 |
| 后端开发 | 2人(100%) | 3人(100%) | API开发、业务逻辑、数据库设计 |
| AI工程师 | 0.5人(50%) | 2人(100%) | AI模型集成、智能功能开发 |
| UI/UX设计师 | 1人(60%) | 1人(40%) | 界面设计、用户体验优化 |
| 测试工程师 | 1人(80%) | 1人(100%) | 功能测试、性能测试、自动化测试 |
| 运维工程师 | 0.5人(50%) | 1人(80%) | 部署运维、监控告警、性能优化 |
| **总计** | **8人当量** | **11.5人当量** | - |

#### 11.3.2 预算规划

| 费用项目 | MVP阶段(4个月) | V2.0阶段(6个月) | 年度运营 | 合计 |
|----------|---------------|-----------------|----------|------|
| 人力成本 | 80万元 | 138万元 | 180万元 | 398万元 |
| 云服务费用 | 8万元 | 12万元 | 24万元 | 44万元 |
| 第三方服务 | 5万元 | 8万元 | 15万元 | 28万元 |
| 硬件设备 | 10万元 | 5万元 | 8万元 | 23万元 |
| 培训推广 | 3万元 | 5万元 | 10万元 | 18万元 |
| 其他费用 | 4万元 | 7万元 | 13万元 | 24万元 |
| **总计** | **110万元** | **175万元** | **250万元** | **535万元** |

### 11.4 推广实施策略

#### 11.4.1 分阶段推广计划

**试点阶段 (2025.12-2026.01)**:
- 选择2个销售团队作为试点用户
- 重点培训核心用户（FAE、销售经理）
- 收集详细的使用反馈和改进建议
- 建立最佳实践案例

**推广阶段 (2026.02-2026.03)**:
- 逐步扩展到所有销售团队
- 组织全员培训和认证
- 建立用户支持体系
- 设立使用激励机制

**优化阶段 (2026.04-2026.06)**:
- 基于用户反馈持续优化
- 推出V2.0高级功能
- 建立长期运营机制
- 评估业务影响和ROI

#### 11.4.2 培训计划

**管理层培训**:
- 时长：4小时
- 内容：产品价值、策略意义、关键指标
- 方式：现场演示+案例分析

**核心用户培训**:
- 时长：2天
- 内容：完整功能演示、实操练习、最佳实践
- 方式：分组培训+实际操作

**普通用户培训**:
- 时长：4小时
- 内容：基本功能使用、常见问题解答
- 方式：在线培训+视频教程

**持续培训**:
- 每月新功能培训
- 季度最佳实践分享
- 年度用户大会

---

## 12. 风险管理与应对

### 12.1 风险识别与评估

| 风险类别 | 风险描述 | 发生概率 | 影响程度 | 风险等级 | 应对策略 |
|---------|---------|---------|---------|---------|---------|
| **技术风险** | AI模型精度不达预期 | 中等 | 高 | 高 | 多模型备选方案，渐进优化 |
| **用户采纳风险** | 用户使用意愿低，习惯难改变 | 高 | 高 | 高 | 激励机制，管理推动 |
| **数据质量风险** | 初期数据质量差，影响AI效果 | 高 | 中等 | 中等 | 数据清洗，专人运营 |
| **集成风险** | 企业微信等外部系统集成困难 | 中等 | 中等 | 中等 | 分阶段集成，备选方案 |
| **性能风险** | 系统性能无法满足并发要求 | 低 | 高 | 中等 | 压力测试，架构优化 |
| **安全风险** | 数据泄露或系统被攻击 | 低 | 高 | 中等 | 安全审计，防护加固 |
| **资源风险** | 关键人员离职影响进度 | 中等 | 高 | 高 | 知识文档化，备份培养 |
| **需求变更风险** | 需求频繁变更影响进度 | 中等 | 中等 | 中等 | 变更控制流程，影响评估 |

### 12.2 详细风险应对计划

#### 12.2.1 技术风险应对

**AI模型精度风险**:
```yaml
应对措施:
  预防:
    - 建立多个AI服务商备选方案(通义千问+Gemini)
    - 设置模型性能基准和监控机制
    - 建立人工审核和纠错机制
  
  缓解:
    - 实施AB测试验证模型效果
    - 建立用户反馈循环改进机制
    - 设置人工智能+"人工"兜底方案
  
  应急:
    - 如果AI效果不佳，先推出人工版本
    - 逐步优化AI模型，分阶段替换
    - 保留手动操作选项作为备份
```

**性能风险应对**:
```yaml
应对措施:
  预防:
    - 系统架构设计考虑水平扩展
    - 早期进行性能基准测试
    - 建立性能监控和告警机制
  
  缓解:
    - 实施缓存策略优化响应时间
    - 数据库查询优化和索引设计
    - CDN加速静态资源访问
  
  应急:
    - 准备快速扩容方案
    - 实施服务降级策略
    - 建立性能问题快速诊断流程
```

#### 12.2.2 业务风险应对

**用户采纳风险**:
```yaml
应对措施:
  预防:
    - 深度参与需求调研，确保产品符合用户需求
    - 设计简单易用的用户界面
    - 建立用户参与产品设计的机制
  
  缓解:
    - 制定详细的用户培训计划
    - 设立使用激励和奖励机制
    - 管理层推动和KPI考核挂钩
  
  应急:
    - 如果采纳率低，深度分析原因
    - 快速迭代改进用户体验
    - 考虑分阶段强制推广策略
```

**数据质量风险**:
```yaml
应对措施:
  预防:
    - 建立数据质量标准和检查机制
    - 设置数据录入规范和模板
    - 建立数据治理和清洗流程
  
  缓解:
    - 安排专门的数据运营人员
    - 建立数据质量监控和报警
    - 实施数据质量奖励机制
  
  应急:
    - 组织专项数据清理行动
    - 暂停依赖数据质量的AI功能
    - 建立数据质量恢复计划
```

### 12.3 风险监控机制

**风险监控指标**:
```yaml
技术指标:
  - API响应时间P99 < 500ms
  - 系统可用性 > 99.9%
  - AI推荐准确率 > 70%
  - 错误率 < 0.1%

业务指标:
  - 月活跃用户率 > 80%
  - 用户满意度NPS > 40
  - 数据完整性 > 95%
  - 培训完成率 > 90%

运营指标:
  - 工单处理时效达标率 > 90%
  - 知识库文章质量评分 > 4.0
  - 系统使用频次持续增长
  - 用户反馈响应时间 < 24h
```

**风险报告机制**:
- 日度风险监控报告（技术指标）
- 周度业务风险评估（用户采纳、数据质量）
- 月度综合风险报告（项目整体风险状态）
- 季度风险回顾和预测（风险趋势分析）

---

## 13. 附录：配置信息与测试数据

### 13.1 系统配置信息

#### 13.1.1 服务器配置
```yaml
production_server:
  ip: 103.251.89.105
  ssh_port: 4100
  os: Ubuntu 22.04 LTS
  specs: 4核8GB RAM
  domain: ai-sensor360.com
  ssl_cert: Let's Encrypt
  
development_server:
  local_env: Docker Compose
  minimum_specs: 2核4GB RAM
  required_ports: [3000, 5432, 6379, 9200, 9000]
```

#### 13.1.2 第三方服务配置
```yaml
ai_services:
  qwen:
    api_key: sk-a7179778042a416591db79a4daf2ffa4
    base_url: https://dashscope.aliyuncs.com/api/v1
    model: qwen-max
    
  gemini:
    api_key: AIzaSyDOV22QEIYPBkBkG7kqja0IS1vzNMn8NC8
    base_url: https://generativelanguage.googleapis.com/v1
    model: gemini-1.5-pro
    
email_service:
  resend:
    api_key: [Your Resend API Key]
    from_domain: ai-sensor360.com
    
wechat_work:
  corp_id: your_corp_id
  agent_id: 1000003
  secret: HtzF5dU7w9YDOUyxz-JILsVONpYtFotQQVrUsECyA3Q
  token: nXhrG0THRecsLBeYRdrgn
  aes_key: ch4moTyQhQgDdzuAyUaHzL3IdKY9s7GwkfvHMLGiQVv
  callback_url: http://ai-sensor360.com:3000/api/wechat/callback

docker_registry:
  mirror: ksveefkaa6do8z.xuanyuan.run
  
pypi_mirror:
  index_url: https://pypi.tuna.tsinghua.edu.cn/simple
  
github_integration:
  token: [Your GitHub Personal Access Token]
```

### 13.2 产品知识库测试数据

#### 13.2.1 昆泰芯微产品系列

**KTH57系列（高性能3D霍尔传感器）**:
```yaml
KTH5701:
  description: 3D霍尔位置传感器芯片，低功耗，高精度，性能全面，支持线性与角度测量
  specifications:
    resolution: 16位
    interface: [SPI, I2C]
    grade: [车规级AQ1, 工业级AQ2, 消费级AQ3]
    applications: [摇杆, 位置检测, 角度测量]
  
KTH5702:
  description: 3D霍尔位置传感器芯片，低功耗，高精度，性能全面，支持线性与角度测量  
  specifications:
    resolution: 16位
    interface: [SPI, I2C]
    grade: [车规级AQ1, 工业级AQ2, 消费级AQ3]
    applications: [摇杆, 位置检测, 角度测量]

KTH5721:
  description: 主打中低速应用场景，单轴最快到7.5KSPS，支持线性与角度测量
  specifications:
    resolution: 16位
    interface: [SPI, I2C]  
    sampling_rate: 7.5KSPS
    grade: [工业级AQ2, 消费级AQ3]
    applications: [中低速位置检测, 角度测量]

KTH5761:
  description: 3D霍尔位置传感器芯片，低功耗，高性价比，支持线性测量
  specifications:
    resolution: 16位
    interface: [I2C]
    grade: [消费级AQ3]
    applications: [线性位置检测]

KTH5762:
  description: 3D霍尔位置传感器芯片，低功耗，高性价比，支持角度测量
  specifications:
    resolution: 16位
    interface: [I2C]
    grade: [消费级AQ3]
    applications: [角度测量]

KTH5763:
  description: 3D霍尔位置传感器芯片，低功耗，高性价比，支持角度测量
  specifications:
    resolution: 8位
    interface: [I2C]
    grade: [消费级AQ3]
    applications: [低精度角度测量]
```

**专用应用系列**:
```yaml
KTH5771:
  description: 3D霍尔位置传感器芯片，摇杆专用芯片
  specifications:
    interface: [模拟接口]
    grade: [消费级AQ3]
    applications: [摇杆控制]

KTH5772:
  description: 3D霍尔位置传感器芯片，游戏摇杆专用芯片
  specifications:
    interface: [I2C, UART]
    grade: [消费级AQ3]
    applications: [游戏手柄摇杆]

KTH5774:
  description: 3D霍尔位置传感器芯片，操纵杆专用芯片
  specifications:
    interface: [I2C, UART, 模拟]
    grade: [消费级AQ3]
    applications: [工业操纵杆]

KTH579x:
  description: 3D霍尔位置传感器芯片，鼠标滚轮专用芯片
  specifications:
    interface: [UART, AB相]
    grade: [消费级AQ3]
    applications: [鼠标滚轮, 编码器]
```

**其他产品系列**:
```yaml
KTH360X:
  description: 数字型线性霍尔传感器芯片，支持I2C/SPI接口
  specifications:
    resolution: 16位
    interface: [I2C, SPI]
    grade: [消费级AQ3]
    applications: [线性Hall传感器应用]

KTH550X:
  description: I2C接口3D霍尔传感器芯片，替代TLV493D、TMAG5373、MT6701
  specifications:
    resolution: 16位
    interface: [I2C]
    grade: [消费级AQ3]
    applications: [3D Hall传感器替代应用]
```

#### 13.2.2 技术支持资料

**驱动程序和开发工具**:
```yaml
drivers:
  KTH57_series:
    i2c_driver: 
      languages: [C, Python, Arduino]
      platforms: [STM32, Arduino, Raspberry Pi]
    spi_driver:
      languages: [C, Python]  
      platforms: [STM32, Arduino]
      
reference_designs:
  joystick_applications:
    - 游戏手柄摇杆参考设计
    - 工业操纵杆解决方案
    - 汽车换挡杆应用方案
  linear_applications:  
    - 线性位移检测方案
    - 阀门位置反馈设计
    - 踏板位置检测方案

development_tools:
  programmer:
    models: [KTH5701, KTH5702, KTH5721, KTH5761, KTH5762]
    software: KTH_Programmer_v2.1.exe
    documentation: KTH编程器使用说明_v2.1.pdf
    
  evaluation_boards:
    KTH57_EVM:
      description: KTH57系列评估板
      software: KTH57_EVM_Software_v1.3.zip
      documentation: KTH57_EVM用户手册_v1.3.pdf
      supported_models: [KTH5701, KTH5702, KTH5721]
```

### 13.3 测试数据集

#### 13.3.1 工单测试数据
```sql
-- 测试工单数据
INSERT INTO tickets (ticket_code, title, description, type, severity, status, product_series, application_domain, created_by) VALUES
('TK2025080001', 'KTH5701传感器输出异常抖动', '客户反馈在游戏手柄摇杆应用中，KTH5701输出信号存在异常抖动，影响用户体验', 'Technical', 'S2-High', 'New', 'KTH57xx', 'Joystick', 1),
('TK2025080002', 'KTH5761 I2C通信失败问题', '客户在工业控制应用中使用KTH5761，出现I2C通信间歇性失败', 'Technical', 'S1-Critical', 'Assigned', 'KTH576x', 'Industrial', 2),
('TK2025080003', '摇杆线性度校准方法咨询', '客户需要了解如何对摇杆应用进行线性度校准和补偿', 'Technical', 'S3-Medium', 'In Progress', 'KTH57xx', 'Joystick', 1),
('TK2025080004', 'KTH579x编码器模式配置', '客户希望将KTH579x配置为增量编码器模式，需要配置指导', 'Technical', 'S3-Medium', 'Resolved', 'KTH579x', 'Mouse Wheel', 3),
('TK2025080005', '竞品TLV493D替代方案', '客户目前使用TI的TLV493D，希望了解昆泰芯微的替代产品方案', 'Commercial', 'S2-High', 'New', 'KTH550x', 'Other', 2);
```

#### 13.3.2 知识库测试数据
```sql
-- 知识库文章测试数据
INSERT INTO knowledge_articles (title, content, category, tags, status, template_type, problem_description, solution_steps, author_id) VALUES
('KTH5701摇杆应用输出抖动问题解决方案', 
 '本文介绍KTH5701在游戏摇杆应用中出现输出抖动的原因分析和解决方法...',
 '技术问题解决', 
 ARRAY['KTH5701', '摇杆', '输出抖动', '游戏手柄'],
 'Published',
 'Problem-Solution',
 '客户反馈KTH5701在摇杆应用中输出信号不稳定，存在明显抖动现象',
 '1. 检查磁铁安装位置和气隙距离\n2. 验证供电电压稳定性\n3. 添加软件滤波算法\n4. 调整传感器增益参数',
 1),

('3D霍尔传感器磁路设计基础指南',
 '本文介绍3D霍尔传感器磁路设计的基本原理和设计要点...',
 '设计指南',
 ARRAY['3D霍尔', '磁路设计', '设计指南'],
 'Published', 
 'Tutorial',
 '如何为3D霍尔传感器设计合适的磁路系统',
 '1. 确定应用类型和测量范围\n2. 选择合适的磁铁材料和尺寸\n3. 计算磁场强度分布\n4. 优化磁铁安装位置',
 2),

('KTH57系列I2C通信调试指南',
 '本文介绍KTH57系列传感器I2C通信的调试方法和常见问题解决...',
 '调试指南',
 ARRAY['KTH57', 'I2C', '通信调试'],
 'Published',
 'Tutorial', 
 '如何调试KTH57系列传感器的I2C通信问题',
 '1. 检查I2C硬件连接\n2. 验证时序参数\n3. 使用逻辑分析仪分析波形\n4. 检查上拉电阻配置',
 1);
```

#### 13.3.3 参考设计测试数据
```sql
-- 参考设计测试数据
INSERT INTO reference_designs (name, description, application_domain, product_series, target_specs, magnetic_config, created_by) VALUES
('游戏手柄摇杆标准方案',
 'Xbox/PlayStation风格游戏手柄摇杆的标准设计方案，包含完整的磁路设计和PCB布局',
 'Joystick',
 'KTH57xx',
 '{"resolution": "16bit", "interface": "I2C", "range": "±30deg", "linearity": "<1%"}',
 '{"magnet_type": "NdFeB N35", "magnetization": "Diametral", "dimensions": "D6xH3mm", "airgap": "1.5mm"}',
 1),

('汽车换挡杆位置检测方案', 
 '汽车自动变速箱换挡杆位置检测的车规级解决方案',
 'Shifter',
 'KTH57xx',
 '{"resolution": "16bit", "interface": "SPI", "range": "Linear 20mm", "temperature": "-40~125°C"}',
 '{"magnet_type": "NdFeB N42SH", "magnetization": "Axial", "dimensions": "D8xH5mm", "airgap": "2.0mm"}',
 2),

('工业阀门位置反馈设计',
 '工业自动化中阀门开度位置反馈的非接触式检测方案', 
 'Industrial',
 'KTH576x', 
 '{"resolution": "16bit", "interface": "I2C", "range": "0~90deg", "protection": "IP67"}',
 '{"magnet_type": "Ferrite", "magnetization": "Radial", "dimensions": "D10xH6mm", "airgap": "3.0mm"}',
 1);
```

### 13.4 企业信息配置

```yaml
company_info:
  name: 昆泰芯微
  website: https://www.conntek.com.cn/
  knowledge_base_path: /Volumes/Web
  
  products:
    primary_series: [KTH55xx, KTH57xx, KTH579x]
    application_domains:
      - Joystick (摇杆)
      - Mouse Wheel (鼠标滚轮) 
      - Pedal (踏板)
      - Steering (方向盘)
      - Shifter (换挡)
      - Seat (座椅)
      - BLDC Position (无刷电机位置)
      - Industrial (工业控制)
      
  target_markets:
    - 汽车电子 (HMI人机交互)
    - 工业自动化 (位置反馈)
    - 消费电子 (游戏设备)
    - 智能家居 (旋钮控制)
    
  key_competitors:
    - AMS (艾迈斯半导体)
    - Infineon (英飞凌)
    - Melexis
    - TI (德州仪器)
    - STMicroelectronics
```

---

**文档结束**

---

**版本历史**:
- V1.0 Final (2025-08-31): 最终整合版本，包含完整功能规划和实施方案

**文档审批**:
- 产品负责人: _________________ 日期: _________
- 技术负责人: _________________ 日期: _________  
- 项目经理: _________________ 日期: _________
- 公司领导: _________________ 日期: _________

**联系方式**:
- 产品咨询: product@gausshub.com
- 技术支持: tech@gausshub.com
- 项目协调: pm@gausshub.com