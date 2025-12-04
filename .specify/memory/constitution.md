<!--
Sync Impact Report:
Version change: 1.0.0 → 1.0.0 (initial creation)
Modified principles: None (initial creation)
Added sections: All sections (initial creation)
Removed sections: None (initial creation)
Templates requiring updates: ✅ plan-template.md, ✅ spec-template.md, ✅ tasks-template.md
Follow-up TODOs: None
-->

# Hidden Bar Constitution

## Core Principles

### I. 代码质量优先 (Code Quality First)
所有代码必须遵循 Swift 编码规范，使用清晰的命名约定，保持适当的函数长度和复杂性。每个类和函数必须有单一职责，避免过度工程化。代码审查是强制性的，所有 PR 必须经过至少一名团队成员的审查才能合并。

### II. 用户体验一致性 (User Experience Consistency)
应用必须保持 macOS 原生体验的一致性，遵循 Apple 人机界面指南。所有 UI 元素必须支持从左到右(LTR)和从右到左(RTL)的语言布局。用户交互必须直观且响应迅速，状态变化必须有明确的视觉反馈。快捷键和菜单项必须遵循 macOS 标准。

### III. 性能优化标准 (Performance Optimization Standards)
应用启动时间必须在 2 秒内完成，菜单栏展开/折叠操作必须在 100ms 内响应。内存使用必须保持在合理范围内，避免内存泄漏。定时器必须正确管理，使用后立即释放。所有异步操作必须适当处理，避免主线程阻塞。

### IV. 测试驱动开发 (Test-Driven Development)
所有新功能必须先编写测试用例，确保测试失败后再实现功能代码。单元测试覆盖率必须达到 80% 以上。关键用户路径必须有集成测试。性能敏感操作必须有基准测试。所有测试必须能够在 CI 环境中稳定运行。

### V. 国际化与可访问性 (Internationalization & Accessibility)
所有用户可见文本必须支持本地化，使用 NSLocalizedString 进行字符串管理。应用必须支持多种语言，包括阿拉伯语等 RTL 语言。UI 元素必须满足可访问性标准，支持 VoiceOver 等辅助技术。图标和颜色选择必须考虑色盲用户的需求。

## 代码结构与组织要求

项目必须遵循清晰的模块化结构，按功能组织代码：
- Features/: 包含独立功能模块
- Extensions/: 包含 Swift 扩展
- Common/: 包含共享工具和常量
- Models/: 包含数据模型
- Views/: 包含自定义视图组件

每个模块必须保持高内聚低耦合，模块间通信必须通过明确的接口进行。避免循环依赖，使用依赖注入管理对象关系。

## 开发工作流程与质量门控

所有开发工作必须遵循 git-flow 工作流程，功能分支命名必须遵循约定。代码提交前必须运行本地测试套件，确保所有测试通过。Pull Request 必须包含清晰的描述，说明变更内容和测试方法。

性能敏感的变更必须包含性能测试结果，确保不影响应用响应速度。UI 变更必须提供截图或视频，展示变更前后的效果。国际化变更必须验证所有支持语言的显示效果。

## Governance

本章程是 Hidden Bar 项目的最高指导原则，所有其他实践和规范都必须遵守。章程的修改需要经过团队讨论，获得多数同意后才能实施。所有代码审查和 PR 合并都必须验证是否符合章程要求。

复杂性的引入必须有明确的理由和文档说明。开发过程中遇到章程未覆盖的情况时，应遵循章程的核心精神，优先考虑用户体验和代码质量。

**Version**: 1.0.0 | **Ratified**: 2025-12-04 | **Last Amended**: 2025-12-04
