# project-chat-orchestrator-skill

本项目维护个人Codex Skill `project-chat-orchestrator`。它让当前主对话在用户确认方案后创建并管理侧边栏中的普通项目对话，分发任务、检查结果和安排返工

## 使用

在目标项目的主对话中明确调用`project-chat-orchestrator`，或明确要求主对话创建其他普通对话执行已确定的方案。执行前需要Codex桌面端可创建普通项目对话、确认项目文件范围及各路径权限。具体触发条件、模型建议、等待方式和任务边界以[Skill源文件](skill/project-chat-orchestrator/SKILL.md)为准

源文件安装到`C:/Users/14672/.agents/skills/project-chat-orchestrator/SKILL.md`。本项目是Codex项目`Test`下的逻辑项目，不要求把本目录另存为独立Codex项目

## 文件入口

- [项目约束](AGENTS.md)：维护范围、禁止项和校验要求
- [Skill源文件](skill/project-chat-orchestrator/SKILL.md)：唯一现行运行规则
- [工作流说明](docs/workflow-spec.md)：对话、项目文件范围和设计关系
- [测试方案与历史结果](docs/test-plan.md)：历史测试、静态检查和待验证事项
- [行为用例](evals/evals.json)、[触发用例](evals/trigger-evals.json)：评测输入，不等于模型运行结果
- [当前接力状态](HANDOFF.md)：当前目标、已完成、待办与风险
- [工作日志](WORKLOG.md)：按时间保存历次修改和验证
- [整理前文档快照](docs/archive/document-management-20260924-before/SNAPSHOT.md)：追溯2026-09-24文档整理前的原件，只读历史

## 维护

修改运行行为时，先读[项目约束](AGENTS.md)，再修改Skill源文件并同步更新受影响的工作流说明、行为评测和触发评测。纯文档整理不安装Skill、不运行模型评测，也不更新真实测试结论
