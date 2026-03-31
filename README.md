# GitCommiter

智能 Git 提交助手 - 分析 staged changes 生成规范 commit message。

## 功能特性

- **智能分析** - 自动分析 staged changes 和历史提交格式
- **格式学习** - 学习项目历史提交的语言风格和格式偏好
- **用户确认** - 生成 message 后展示预览，征询用户确认后才提交
- **安全防护** - 自动检测敏感文件，避免误提交

## 快速开始

### 1. 安装 Skill

将 `SKILL.md` 放入 OpenCode 的 skills 目录：

```
~/.config/opencode/skills/gitcommiter/SKILL.md
```

### 2. 使用方式

在 OpenCode 中加载 skill 后：

```
用户: 帮我提交
助手: 正在分析 staged changes...
      生成的 commit message：
      feat: 添加用户登录功能

      [Y] 确认提交 [N] 取消
用户: Y
助手: 提交成功！
```

## 提交格式

```
<type>: <subject>

<body>

【type类型】
```

**示例：**

```
feat: 添加用户登录功能

本次提交添加了用户登录功能：
1. 添加用户名密码验证
2. 集成 JWT token

【type类型】
feat | fix | docs | style | refactor | test | chore | perf | ci | build
```

## Type 类型

| Type | 说明 |
|------|------|
| `feat` | 新功能 |
| `fix` | 修复 bug |
| `docs` | 文档更新 |
| `style` | 代码格式 |
| `refactor` | 重构 |
| `test` | 测试 |
| `chore` | 杂务/维护 |
| `perf` | 性能优化 |
| `ci` | CI 配置 |
| `build` | 构建/依赖 |

## 工作流程

```
检测 staged changes → 分析 diff → 学习历史格式 → 生成 message → 用户确认 → 执行提交
```

## 安全机制

- 自动检测敏感文件（.env、secrets 等）
- 敏感文件误提交前会警告用户
- 必须用户确认后才执行提交

## 配置说明

Skill 会自动：
- 分析最近 20 条历史提交
- 学习项目的语言风格（中文/英文）
- 根据文件路径自动推断 scope

无历史记录时会询问用户偏好。

## 相关命令

```bash
# 查看 staged 改动
git diff --cached

# 查看状态
git status

# 查看最近提交
git log --oneline -5
```
