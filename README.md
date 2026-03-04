# TerminalLauncher v2.0
轻量级 Windows 终端快速启动工具 | 单文件 0.05MB 

## 🌟 核心功能
| 功能分类       | 具体能力                                                                 |
|----------------|--------------------------------------------------------------------------|
| 快速启动       | 一键启动 CMD/PowerShell/Windows Terminal/Git Bash（普通/管理员模式）|
| 全局热键       | 自定义全局热键，支持「工作/个人」两套热键分组一键切换                     |
| 目录管理       | 常用目录收藏/编辑/删除，拖放文件/目录直接在对应路径启动终端               |
| 快捷命令       | 自定义快捷命令（如 ipconfig、ping 等），一键执行（适配不同终端类型）|
| 会话记忆       | 自动记录上次启动的终端类型和目录，支持一键恢复                           |
| 终端定制       | 自定义终端背景色、字体大小（修改系统控制台配置）|
| 系统集成       | 开机自启、终端窗口置顶、防止多开、启动日志记录                           |
| 配置管理       | 配置导入/导出、恢复默认配置，支持命令行参数启动（-silent/-dir）|


## 🚀 使用说明
### 1. 基础启动
- 双击 `TerminalLauncher.exe` 即可启动，程序会最小化到系统托盘（无主窗口）
- 防止多开：重复启动会提示「已在运行中」
- 静默启动：`TerminalLauncher.exe -silent`（无弹窗提示）
- 指定目录启动：`TerminalLauncher.exe -dir "D:\Projects"`（在指定目录启动默认终端）

### 2. 托盘右键菜单
右键点击系统托盘图标，可操作以下功能：
- **快速启动终端**：桌面/文档/自定义目录/常用目录
- **快捷命令**：执行已配置的自定义命令
- **配置管理**：导出/导入/恢复默认配置
- **设置默认终端**：CMD/PowerShell/Windows Terminal 三选一
- **高级功能**：恢复上次会话/切换热键分组/设置终端样式/清空日志
- **基础设置**：终端窗口置顶/开机自启
- **其他**：重启程序/退出

### 3. 全局热键（默认）
| 热键          | 功能                     | 工作分组（默认） | 个人分组       |
|---------------|--------------------------|------------------|----------------|
| 启动 CMD      | 普通模式                 | Alt+C            | Ctrl+C         |
| 启动 CMD      | 管理员模式               | Alt+A            | Ctrl+A         |
| 启动 PowerShell| 普通模式                | Alt+P            | Ctrl+P         |
| 启动 PowerShell| 管理员模式              | Alt+D            | Ctrl+D         |
| 启动 WT       | 普通模式                 | Alt+W            | Ctrl+W         |
| 启动 WT       | 管理员模式               | Alt+S            | Ctrl+S         |
| 启动 Git Bash | 普通模式                 | Alt+G            | Ctrl+G         |
| 启动 Git Bash | 管理员模式               | Alt+H            | Ctrl+H         |
| 复制路径      | 复制当前资源管理器路径   | Alt+V            | Ctrl+V         |
| 恢复上次会话  | 恢复上次启动的终端/目录  | Alt+Z            | Ctrl+Z         |
| 切换热键分组  | 工作 ↔ 个人              | Alt+F            | Ctrl+F         |
| 退出程序      | 关闭 TerminalLauncher    | Alt+X            | Ctrl+X         |

### 4. 常用目录管理
- **添加**：托盘菜单 → 快速启动终端 → 常用目录 → 添加常用目录
- **编辑/删除**：托盘菜单 → 快速启动终端 → 常用目录 → 编辑/删除
- 配置文件：`FavDirs.ini`（格式：`目录名称=目录路径`）

### 5. 快捷命令管理
- **添加**：托盘菜单 → 快捷命令 → 添加快捷命令
  - 命令名称：自定义（如「查看IP」）
  - 命令内容：终端命令（如 `ipconfig /all`）
  - 终端类型：0=CMD，1=PowerShell，2=Windows Terminal
- 配置文件：`QuickCmds.ini`（格式：`命令名称=命令内容|终端类型`）

### 6. 高级功能
- **恢复上次会话**：自动记忆上次启动的终端类型和目录，一键恢复
- **切换热键分组**：工作/个人两套热键配置，切换后立即生效
- **设置终端样式**：修改终端背景色（十进制RGB）、字体大小，下次启动生效
- **启动日志**：自动记录终端启动记录，日志文件 `TerminalLauncher.log`

## ⚙️ 配置说明
### 配置文件
- 工作分组配置：`config_work.ini`
- 个人分组配置：`config_personal.ini`
- 配置文件自动生成，无需手动创建

### 核心配置项说明
| 配置节       | 配置项          | 说明                          |
|--------------|-----------------|-------------------------------|
| [Window]     | X/Y/Width/Height| 终端窗口位置和大小            |
| [Config]     | TopMost         | 终端窗口置顶（0=否，1=是）|
| [Config]     | AutoStartup     | 开机自启（0=否，1=是）|
| [Config]     | DefaultTerminal | 默认终端类型（0=CMD，1=PS，2=WT） |
| [Style]      | BgColor         | 终端背景色（十进制RGB）|
| [Style]      | FontSize        | 终端字体大小（10-20 推荐）|
| [Session]    | LastDir         | 上次启动目录                  |
| [Session]    | LastType        | 上次启动终端类型              |

## ❓ 常见问题
### 1. 热键冲突
- 程序启动时会检测热键冲突，弹窗提示冲突的热键
- 可修改配置文件中 `HotKeyGroup_Work`/`HotKeyGroup_Personal` 节的热键值
  - Mod 值：1=Alt，2=Ctrl，4=Shift
  - Key 值：按键的 ASCII 码（如 C=67，A=65）

### 2. 找不到 Windows Terminal/Git Bash
- Windows Terminal：自动检测 `%LOCALAPPDATA%\Microsoft\WindowsApps\wt.exe`
- Git Bash：自动检测 `C:\Program Files\Git\bin\bash.exe`（32位/64位）
- 若未找到，可手动在配置文件中填写路径

### 3. 管理员权限启动失败
- Windows UAC 权限限制，需手动允许程序以管理员身份运行
- 或右键程序 → 属性 → 兼容性 → 勾选「以管理员身份运行此程序」


## 下载
### [releases](https://github.com/nehciuruil/TerminalLauncher/releases)

**本README文件由DoubaoAI看代码编写。**
