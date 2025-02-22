---
sidebar_position: 7
---
# Destroy

通过工作目录销毁已应用到资源的配置栈

### Synopsis

通过资源规约删除资源。

只接受 KCL 文件。只能指定一种类型的参数：文件名、资源、名称、资源或标签选择器。

请注意，destroy 命令不会进行资源版本检查， 因此如果有人在你提交销毁时提交了对资源的更新， 他们的更新将与资源一起丢失。

```
kusion destroy [flags]
```

### Examples

```
  # Delete the configuration of current stack
  kusion destroy
```

### Options

```
  -D, --argument strings    指定编译 KCL 的参数
  -d, --detail              预览后自动展示 apply 计划细节
  -h, --help                help for destroy
      --operator string     指定操作人
  -O, --overrides strings   指定配置覆盖路径和值
  -Y, --setting strings     指定命令行配置文件
  -w, --workdir string      指定工作目录
  -y, --yes                 预览后自动审批并应用更新
```

### Options inherited from parent commands

```
      --log-level string        设置 kusion 开发日志级别，默认为 INFO，所有选项：DEBUG、INFO、ERROR、WARN、FATAL (default "INFO")
      --profile string          要捕获的档案名称。none、cpu、heap、goroutine、threadcreate、block 和 mutex 之一 (default "none")
      --profile-output string   档案写入的文件名 (default "profile.pprof")
```

### SEE ALSO

* [kusion](./overview.md)	 - kusion 通过代码管理 Kubernetes

###### Auto generated by spf13/cobra on 21-Jan-2022
