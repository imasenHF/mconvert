# Mconvert

Mconvert 是一个调用 Multiwfn 交互式导出功能的 Bash 包装脚本，用于批量或单文件转换化学结构与波函数文件，并可按模板生成 Gaussian / ORCA 输入文件。

这是一个历史工具项目，仓库保留整理后的脚本与使用说明，不另设项目主页。

公开署名：hyphoon  
联系：wuhaifeng@ustc.edu.cn

## 依赖

- Bash
- Multiwfn

默认直接调用 `Multiwfn`。如果 Multiwfn 不在 `PATH`，可指定：

```bash
export MULTIWFN_BIN=/path/to/Multiwfn
```

Windows 可在 Git Bash、WSL 等 Bash 环境中运行。

## 安装

```bash
chmod +x Mconvert
```

随后将脚本所在目录加入 `PATH`，或直接以相对/绝对路径运行。

## 批量转换

```bash
Mconvert <input_ext>2<output_ext>
```

例如：

```bash
Mconvert log2xyz
Mconvert log2pdb
Mconvert fchk2molden
Mconvert log2oif
```

`oif` 表示 ORCA input file，实际输出文件使用 `.inp` 后缀。

## 单文件转换

```bash
Mconvert Benzene.fchk Benzene.molden
Mconvert Benzene.log Benzene.xyz
Mconvert Benzene.log Benzene.inp
```

## 生成输入模板

```bash
Mconvert gau_template
Mconvert orca_template
```

默认 Gaussian / ORCA 模板只是工作示例，计算方法、基组、溶剂、CPU 核数、内存、电荷与多重度均应按实际任务检查。

## 支持的输出类型

当前脚本封装：

`pqr`、`pdb`、`xyz`、`chg`、`wfx`、`wfn`、`molden`、`fch/fchk`、`47`、`mkl`、`cml`、`mwfn`、`cif`、`gro`、`gjf` 与 ORCA input。

这些映射依赖 Multiwfn 主功能 `100 → 2` 的交互菜单编号。Multiwfn 版本变化后应重新检查菜单顺序和转换结果。

## 项目来源

历史介绍：

- 计算化学公社：http://bbs.keinsci.com/thread-39972-1-1.html
- 相关 Multiwfn 批处理思路：http://sobereva.com/530

Mconvert 本身不实现格式解析，实际转换由 Multiwfn 完成。科研使用时请同时遵循所用 Multiwfn 版本的引用要求。

## License

当前未设置开源许可。
