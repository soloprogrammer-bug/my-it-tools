1. 项目基本信息
项目	详情
仓库地址	https://github.com/CorentinTh/it-tools
技术栈	Vue 3 + Vite + TypeScript + Tailwind CSS
包管理器	pnpm
许可证	GNU GPLv3
当前用户环境	Windows, Node.js v24.14.0

2. 前置环境准备
2.1 环境检查清单
在开始之前，请确保以下环境已就绪：
✅ Windows 10/11 操作系统
✅ Node.js v24.14.0（用户已确认）
✅ Git 已安装并配置
⏳ pnpm 包管理器（需要安装）
2.2 安装 pnpm
如果尚未安装 pnpm，请在 PowerShell 或 Git Bash 中执行：
# 使用 npm 安装 pnpm
npm install -g pnpm

# 验证安装
pnpm -v

3. 完整从零开始的构建步骤
3.1 第一步：创建工作目录并克隆仓库
在您想要存放项目的位置（例如 C:\Projects\），执行以下命令：
powershell
# 创建并进入工作目录
mkdir ITTools
cd ITTools

# 克隆仓库
git clone https://github.com/CorentinTh/it-tools.git
cd it-tools
3.2 第二步：安装项目依赖
powershell
# 在 it-tools 目录下执行
pnpm install
预期结果：
pnpm 会读取 pnpm-lock.yaml 文件
安装所有依赖到 node_modules 目录
安装过程可能需要 2-5 分钟，取决于网络速度
常见问题处理：
如果遇到网络超时，配置 pnpm 使用淘宝镜像：
powershell
pnpm config set registry https://registry.npmmirror.com
如果安装失败，删除 node_modules 和 pnpm-lock.yaml 后重试

3.3 第三步：启动开发服务器
powershell
pnpm dev
预期结果：
Vite 开发服务器启动成功
终端显示类似以下输出：
plaintext
VITE v5.x.x  ready in xxx ms

➜  Local:   http://localhost:5173/
➜  Network: use --host to expose
浏览器会自动打开 http://localhost:5173/
支持热模块替换（HMR），修改代码后页面会自动刷新
3.4 第四步：验证项目功能
在浏览器中打开 http://localhost:5173/，请验证以下核心功能：
✅ 页面正常加载，显示工具列表
✅ 点击任意工具（如 JSON 格式化），工具页面正常显示
✅ 测试工具功能是否正常工作
✅ 尝试切换明暗主题（右上角）
✅ 尝试切换语言（如果支持）
3.5 第五步：生产环境构建（可选，用于验证）
powershell
pnpm build
预期结果：
在项目根目录生成 dist 文件夹
包含完整的生产环境静态文件
构建过程可能需要 1-3 分钟
4. 项目结构深度解析
构建成功后，请熟悉以下关键目录和文件，为二次开发做准备：
plaintext
it-tools/
├── src/
│   ├── tools/              # 所有工具组件的存放位置（二次开发重点）
│   │   ├── json-formatter/ # JSON 格式化工具示例
│   │   ├── base64/         # Base64 编解码工具
│   │   └── index.ts        # 工具注册入口
│   ├── components/         # 通用 UI 组件
│   ├── styles/             # 全局样式
│   └── main.ts             # 应用入口
├── locales/                # 国际化语言文件
├── public/                 # 静态资源
├── vite.config.ts          # Vite 构建配置
├── package.json            # 项目依赖和脚本
└── pnpm-lock.yaml          # pnpm 锁定文件
关键文件说明
src/tools/index.ts: 所有工具的注册中心，添加新工具需要在这里导入
vite.config.ts: Vite 配置文件，包含构建、代理等配置
package.json: 包含所有可用的脚本命令
5. 二次开发准备
5.1 了解如何创建新工具
项目提供了自动化脚本生成新工具的模板：
powershell
pnpm run script:create:tool my-custom-tool
这会自动：
在 src/tools/ 下创建新工具目录
生成基础的 Vue 组件文件
在 src/tools/index.ts 中自动导入
5.2 推荐的 VS Code 插件
为了获得最佳开发体验，请安装以下插件：
Volar（Vue 3 官方推荐，禁用 Vetur）
TypeScript Vue Plugin (Volar)
ESLint
i18n Ally
5.3 配置 VS Code 设置
在项目根目录创建 .vscode/settings.json（如果不存在），添加以下配置：
json
{
  "editor.formatOnSave": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "i18n-ally.localesPaths": ["locales", "src/tools/*/locales"],
  "i18n-ally.keystyle": "nested"
}
6. 可用的 npm/pnpm 脚本
表格
命令	说明
pnpm dev	启动开发服务器
pnpm build	构建生产版本
pnpm preview	预览生产构建
pnpm test	运行单元测试
pnpm lint	运行 ESLint 检查
pnpm run script:create:tool <name>	创建新工具模板
7. 常见问题排查（Windows 专属）
7.1 Node.js 版本兼容性
虽然用户使用的是 v24.14.0，但项目推荐 v18.18.2。如果遇到兼容性问题：
使用 nvm-windows 管理 Node.js 版本
或者尝试在 package.json 中移除 engines 字段限制
7.2 路径问题
Windows 路径分隔符可能导致问题：
推荐使用 Git Bash 而不是 PowerShell
确保项目路径中不包含中文字符或空格
7.3 端口被占用
如果 5173 端口被占用：
Vite 会自动尝试下一个可用端口（5174, 5175...）
或者在 vite.config.ts 中配置默认端口
7.4 依赖安装失败
powershell
# 清理缓存
pnpm store prune

# 删除依赖并重新安装
Remove-Item -Recurse -Force node_modules
Remove-Item pnpm-lock.yaml
pnpm install
8. 下一步：二次开发建议
构建成功并验证项目正常运行后，您可以：
熟悉现有工具代码：查看 src/tools/ 下的几个核心工具，了解项目的代码风格和架构
尝试创建一个简单的测试工具：使用 pnpm run script:create:tool 创建一个新工具，熟悉开发流程
规划您的自定义功能：
是否需要添加 API 测试功能（类似 Postman）？
是否需要添加新的编解码工具？
是否需要集成 Python 后端？
9. 验证清单
在继续二次开发之前，请确认您已完成以下所有步骤：
✅ 成功克隆仓库
✅ 成功安装所有依赖
✅ 成功启动开发服务器
✅ 浏览器能正常访问 http://localhost:5173/
✅ 测试了至少一个工具的功能
✅ 了解了项目的基本目录结构
✅ 知道如何创建新工具