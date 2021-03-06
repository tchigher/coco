# Coco

![Coco Build](https://github.com/phodal/coco/workflows/Coco%20Build/badge.svg)

> (aka coconut, juice), an automatic DevOps metrics analysis tool.

特性（features in Chinese）：

 - 改进建议（英语）
 - 框架检测
 - 分支生命周期和可视化
 - 云原生成熟度分析
 - 团队健康值分析
 - 图形可视化
 - 多项目**并行**分析

features:

 - automatic suggestion (online).
 - framework detector
 - branch lifecycle and visual
 - cloud-native analysis
 - team health analysis
 - graph visual and reporter
 - multiple-repo **parallel**

## Usage

1. create `coco.yml` in projects.
2. config `coco.yml`
3. run `coco`

### coco.yml

#### 配置 (config in Chinese)

示例：

```yml
# 代码库
repo:
  - url: https://github.com/coco-rs/coco.fixtures
  - url: https://github.com/coco-rs/coco.fixtures2

# 提交信息格式
commit-message:
  # default: conventional commit: (?<type>build)(?<scope>(?:\([^()\r\n]*\)|\()?(?<breaking>!)?)(?<subject>:.*)?
  # jira: ^(feature|fix)\/(([a-z,A-Z]+))(-)(\d*)(:)([a-z,0–9])
  # jira test case: feature/JIR-124:test commit message
  regex: ^(feature|fix)\/(([a-z,A-Z]+))(-)(\d*)(:)([a-z,0–9])
  matches:
    - branch
    - tag
    - id
  samples: feature/JIR-124:test commit message
```

#### Config

## Development

IDE: Clion

### Setup

1.install Rust

follow [https://www.rust-lang.org/tools/install](https://www.rust-lang.org/tools/install)

2.install `justfile`

follow: [https://github.com/casey/just](https://github.com/casey/just)

3.Run tests

```
just tests
```

4.test Command

```
cargo run --bin coco
```

#### Setup for Windows Subsystem for Linux (Debian)

1. install rust

```
apt-get install curl
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

2. install just

```
cargo install just
```

3. install dependency package

```
sudo apt-get install gcc cmake g++ pkg-config libssl-dev 
sudo apt-get install libfreetype6-dev expat libxml2 libasound2-dev libexpat1-dev libxcb-composite0-dev
```

4. Run tests

```
just tests
```

#### Setup for macOS with HomeBrew

1. install rust

```
brew install rustup
rustup-init
```
重启shell，或者执行``` source $HOME/.cargo/env ```


2. install just

```
brew install just
```

3.Run tests

```
just tests
```


### Architecture

![Architecture](docs/images/coco-architecture.svg)

third-party libs:

 - libgit2, git api
 - tokei, cloc api

## Documents

### Online video

Bilibili: [研发效能分析工具 Coco 第一次线上讨论](https://www.bilibili.com/video/BV18K4y1W7jN/)

### Roadmap

#### analysis and reporter

analysis

 - git analysis
    - branch
    - changes
    - commits
 - cloc analysis
    - summary
    - file arch
 - framework analysis
 - architecture analysis
    - file/directory organization

reporter

 - html reporter
 - json output
 - query api?

#### suggest and case study


## Todo

 - [x] git analysis
    - [x] merge code from [coca](https://github.com/phodal/coca/tree/master/pkg)
 - [ ] git tag analysis
    - [x] git branch analysis
       - [x] branch history
    - [ ] git commit time analysis
       - [ ] storage all commits
          - [ ] light database?
       - [ ] working night count
 - [ ] cloc analysis
    - [x] spike cloc tools [Tokei](https://github.com/XAMPPRocky/tokei)
    - [ ] history cloc changes
    - [ ] commit cloc changes
 - [ ] framework detector.
    - [x] merge from [scie-detector](https://github.com/datum-lang/scie/tree/master/scie-detector)
    - [ ] framework output
 - [ ] module analysis
    - [ ] base framework for directory
       - [ ] gitignore support
    - [ ] code flower
 - [ ] team analysis
    - [ ] join time & life time
    - [ ] member growth
    - [ ] count system size & learning curve
 - [ ] commit analysis
    - [ ] rule regex support in config
    - [ ] participle（分词）
    - [ ] tags generate
 - [ ] suggestion API
    - [ ] suggest ledge
    - [ ] suggest phodal
    - [ ] online suggest
       - [ ] link daily checkx
 - [ ] graph support for velocity
    - [ ] code commits by daily
    - [ ] PR times by daily
 - [ ] tech stack generate
 - [ ] cloud native
    - [ ] dockerfile analysis
 - [ ] tools
    - [ ] tools config identify
    - [ ] tools suggest (identify old tools)
    - [ ] cloud-native config
 - [ ] case study
 - [ ] jenkins api analysis
 - [ ] story velocity
    - [ ] commit message analysis
    - [ ] story spend days

Visual and Reporter

 - visual
     - [ ] spike d3.js code organization
     - [ ] architecture
         - [ ] code flower, examples: [Polyglot Code Explorer](https://blog.korny.info/2020/09/06/introducing-the-polyglot-code-explorer.html), [D3.js code flower](https://github.com/fzaninotto/CodeFlower)
     - [ ] git
         - [ ] branch history
 - [ ] reporter
     - [ ] framework
     - [ ] cloc
     - [ ] git
     - [ ] architecture

## Documents

Refs: [Libgit2 Documents](https://github.com/libgit2/libgit2.github.com/blob/master/docs/guides/101-samples/index.md)

License
---

[![Phodal's Idea](http://brand.phodal.com/shields/idea-small.svg)](http://ideas.phodal.com/)

@ 2020~2021 A [Phodal Huang](https://www.phodal.com)'s [Idea](http://github.com/phodal/ideas).  This code is distributed under the MIT license. See `LICENSE` in this directory.
