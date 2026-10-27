# catastrophic

**检测微调后原能力是否退化。**

`catastrophic` —— 比较微调前后在原任务上的表现，标出退化项与幅度

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`catastrophic.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install pkilton-catastrophic
```

装完直接用命令名调用：

```bash
catastrophic --help
```

也可以不用安装，直接把 `catastrophic.py` 拷走用——它只依赖标准库。

## 为什么需要它

要有一组不退化的基线任务，否则无从判断

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 灾难性遗忘 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python catastrophic.py --file input.txt
python catastrophic.py --text "示例内容"
python catastrophic.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 分箱是等宽或等频，样本太少时结论不稳。
- 不做显著性检验。

## 跑测试

```bash
python test_catastrophic.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/pkilton/catastrophic>

---

## 关于作者

pkilton 做灾难性遗忘相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://pkilton.github.io>
- 仓库：<https://github.com/pkilton/catastrophic>

## 许可

MIT，见 [LICENSE](LICENSE)。
