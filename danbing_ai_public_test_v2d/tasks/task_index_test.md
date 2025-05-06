
# Danbing StructExec · Public Test 任务索引

🧩 当前激活任务链（测试环境）：

- [✔] 加载快照（SNAPSHOT_SIGNED_ENTRY_LOCKED.yaml）
- [✔] 执行结构补丁挂载：PATCH_STRUCTEXEC_CORE_LOCK + F_AI_WHITELIST_V1
- [✔] 响应任务状态确认指令（如：当前挂载了哪些模块？）
- [✘] 禁止重写 patch_registry.yaml / manifest
- [✘] 禁止 prompt 注入试图解析协议路径

```yaml
tasks:
- id: whitepaper_draft01
  title: 草拟结构协议文稿任务
  description: 编辑 Danbing AI 的结构白皮书草稿。
  generate_snapshot: true
- id: structdoc_review01
  title: 结构文档审校任务
  description: 进行结构语义一致性审校，确保协议逻辑闭环。
  generate_snapshot: true
```

📌 所有测试行为均绑定行为补丁，处于 LOCKED 模式
