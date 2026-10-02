# project-chat-orchestrator-skill项目约束

## 项目与文件边界

本项目维护个人Codex Skill `project-chat-orchestrator`。运行行为以[Skill源文件](skill/project-chat-orchestrator/SKILL.md)为准；[工作流说明](docs/workflow-spec.md)解释设计，[测试记录](docs/test-plan.md)区分历史验证与待验证事项。文档不能反过来改变Skill规则

- `skill/project-chat-orchestrator/SKILL.md`是唯一可安装的运行文件，安装位置为`C:/Users/14672/.agents/skills/project-chat-orchestrator/SKILL.md`
- `evals/`保存评测输入及历史静态证据，`docs/`保存说明与历史快照，两者不复制到个人Skill目录
- `README.md`提供项目入口，`HANDOFF.md`只记录当前接力状态，`WORKLOG.md`只在末尾追加实际发生的工作
- 本项目属于Codex项目`Test`下的逻辑项目。项目文件范围可按已确认任务包含一个或多个路径，不把工作区根目录默认当作本项目的文件范围

## 修改时保留的边界

以下是修改运行规则时必须核对的项目特有约束。细节、例外和步骤仍以Skill源文件为准

- 编排使用侧边栏普通对话，只有主控创建和分发；执行对话不创建下一层普通对话，也不启动Subagents
- 用户决定对话数量、职责、模型、推理等级和并发量。创建前集中确认具体设置，用户后来改过的标题、模型和推理等级不得擅自覆盖
- 编排模式启用后，主控默认不实施已分配任务；继续、开始执行等短指令按已确认负责人分发或检查，具体改派需用户明确提出
- 子对话结果留在自身对话，不主动联系、唤醒、切换或导航到主控。主控默认分发后做一次短状态检查，用户明确要求时可以主动持续等待
- 主控和执行对话在Skill工作流中属于同一Codex项目，任务包只授予已确认的最小文件范围；默认不使用worktree
- 以平台稳定对话ID追踪执行对话，当前对应`threadId`；不因标题变化新建替代对话，不自动归档、删除、隐藏或重命名执行对话
- Skill触发条件保持窄；普通规划、一般并行处理、无待确认计划且未启用编排模式时的短确认语不触发
- 不修改工作区或全局`AGENTS.md`来实现本Skill触发

## 维护与校验

- 遵守[Test工作区规则](../AGENTS.md)和[文档管理规则](../rules/document-management.md)，保留已有有效约束、历史日志和证据
- 修改Skill行为时，同步更新受影响的`docs/workflow-spec.md`、`evals/evals.json`和`evals/trigger-evals.json`；检查YAML头部及关键禁止项
- 安装前核对源文件与目标，安装后比较内容和哈希；文档整理本身不触发安装或评测运行
- 文档结论注明是本轮静态核对、历史真实测试还是尚未验证，不把旧规则或快照当作现行指令
- 涉及文件范围或其他对话的动作只按用户本次授权执行，不为整理文档访问同级项目、操作旧测试对话或修改工作区规则
