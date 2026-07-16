# rCore OS Training Camp

基于 [rCore-Tutorial-Code](https://github.com/LearningOS/rCore-Tutorial-Code) 的 Rust 操作系统实验训练环境。

本仓库用于完成 rCore 操作系统实验。每个实验章节对应一个 Git 分支，学生完成实验后提交代码，GitHub Actions 会自动运行测试并生成成绩。

---

# 1. 实验流程

本训练营采用：

```
个人仓库
   |
   |
选择实验分支(ch1~ch9)
   |
   |
完成实验代码
   |
   |
git push
   |
   |
GitHub Actions 自动测试
   |
   |
查看实验成绩
```

---

# 2. Repository Structure

每个章节对应一个独立分支：

| 分支 | 实验章节 | 测试方式 |
|---|---|---|
| `ch1` | 应用程序与裸机环境 | 编译检查 |
| `ch2` | 批处理系统 | 编译检查 |
| `ch3` | 多道程序与系统调用 | 自动测试 |
| `ch4` | 地址空间 | 自动测试 |
| `ch5` | 进程管理 | 自动测试 |
| `ch6` | 文件系统 | 自动测试 |
| `ch7` | 进程间通信 | 自动测试 |
| `ch8` | 并发与同步 | 自动测试 |
| `ch9` | 后续扩展实验 | 自动测试 |

---

# 3. Learning Resources

## rCore Tutorial Source Code

https://github.com/LearningOS/rCore-Tutorial-Code


## rCore Tutorial Guide

https://LearningOS.github.io/rCore-Tutorial-Guide/


## rCore Tutorial Book

https://rcore-os.github.io/rCore-Tutorial-Book-v3/


---

# 4. Environment Setup

## Requirements

推荐环境：

- Linux
- Ubuntu 20.04 / 22.04 / 24.04

需要安装：

- Rust nightly
- QEMU
- RISC-V Rust target


## Install Rust

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```


## Install RISC-V Target

```bash
rustup target add riscv64gc-unknown-none-elf
```

---

# 5. Clone Your Repository

请使用训练营提供的个人仓库地址。

例如：

```bash
git clone https://github.com/<YOUR_USERNAME>/<YOUR_REPOSITORY>.git

cd <YOUR_REPOSITORY>
```

---

# 6. Start an Experiment

每个章节对应一个 Git 分支。

例如完成第三章：

```bash
git checkout ch3
```

进入内核目录：

```bash
cd os
```

运行操作系统：

```bash
make run
```

---

# 7. Submit Your Work

完成实验后：

```bash
git add .

git commit -m "finish ch3"

git push origin ch3
```

注意：

- 每个章节提交到对应分支；
- 不要提交到 `main`；
- GitHub Actions 会自动检测对应分支。


例如：

```
ch3 branch

      |
      |
      v

 git push

      |
      |
      v

GitHub Actions

      |
      |
      v

自动测试并生成成绩
```

---

# 8. Check Your Score

提交完成后：

进入仓库：

```
Actions
    |
    |
选择对应章节测试
    |
    |
查看 Summary
```

测试结果示例：

```
# 🎯 Test Result

| Item | Result |
|---|---|
| Passed Tests | 10/10 |
| Score | 10/10 |

Status: PASS
```

如果测试失败：

进入：

```
Actions
    |
    |
对应测试任务
    |
    |
Logs
```

查看详细错误信息。

---

# 9. Local Test (Optional)

如果希望提交前本地测试，可以安装测试工具：

```bash
git clone https://github.com/LearningOS/rCore-Tutorial-Checker.git ci-user

git clone https://github.com/LearningOS/rCore-Tutorial-Test.git ci-user/user
```

例如测试第三章：

```bash
cd ci-user

make test CHAPTER=3
```

其他章节：

```bash
make test CHAPTER=4

make test CHAPTER=5

make test CHAPTER=6
```

---

# 10. Docker Environment (Optional)

如果本地环境配置困难，可以使用 Docker。

构建环境：

```bash
make build_docker
```

运行环境：

```bash
make docker
```

---

# 11. Grading Rules

每个章节独立评分：

- GitHub Actions 自动执行测试；
- 测试结果显示通过数量；
- 成绩显示在 Actions Summary。


评分流程：

```
代码提交
    |
    |
GitHub Actions
    |
    |
自动测试
    |
    |
生成成绩
```

---

# 12. FAQ

## Q1: 为什么 push 后没有触发测试？

检查当前分支：

```bash
git branch
```

例如第三章应该：

```
* ch3
```

检查是否已经提交：

```bash
git status
```

然后重新 push：

```bash
git push origin ch3
```

---

## Q2: 可以提交 main 分支吗？

不建议。

`main` 用于保存：

- README
- 课程说明
- 公共配置

实验代码请提交：

```
ch1
ch2
ch3
...
ch9
```

---

## Q3: 为什么本地可以运行，但是 Actions 失败？

可能原因：

- Rust 版本不同；
- 缺少 RISC-V target；
- QEMU 环境不同；
- 实验代码依赖本地环境。


建议：

优先查看 GitHub Actions 日志。

---

# License

MIT License
