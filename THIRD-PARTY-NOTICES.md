# 第三方组件与许可声明

本项目主体代码以 **AGPL-3.0** 授权（见根目录 `LICENSE`）。下列第三方组件仍遵循其各自的原许可，不受 AGPL-3.0 替代。

## 组件清单

| 组件 | 版本 | 许可 | 版权行 | 是否随发布物分发 | 声明状态 |
| --- | --- | --- | --- | --- | --- |
| three.js（核心库） | r160（源码内 `REVISION` 为 `"160"`） | MIT | `Copyright 2010-2023 Three.js Authors` | 是，内联于 `index.html` 第 605–2191 行 | 文件头许可注释已保留，本文补充独立声明 |
| three.js 后期处理附加模块：`EffectComposer`、`RenderPass`、`UnrealBloomPass`、`OutputPass`、`ShaderPass`、`FXAAShader` | 同 r160 | MIT | 同上 | 是，内联于同一段脚本 | 同上 |
| FXAA 3.11 着色器（由 NVIDIA 实现，Agost Biro 移植到 WebGL，经 three.js 分发） | FXAA 3.11 / SDK v3.00 | BSD-3-Clause（NVIDIA） | `Copyright (c) 2014-2015, NVIDIA CORPORATION. All rights reserved.` | 是，内联于 `index.html` 第 1047–1080 行 | 许可全文随源码保留 |

## 引入方式核实

- 项目**没有** `package.json`、lockfile、`node_modules` 或 `vendor/` 目录，也不是通过 npm 安装依赖。
- `index.html` 中**没有**任何 `<script src>`、`<link href>`、CDN 地址或 `import` 语句。
- three.js r160 及其后期处理模块被整体内联在 `index.html` 的第二个 `<script>` 中（第 605 行开始），因此页面在断网、`file://` 和微信内置浏览器下都能直接运行。
- 发布物就是 `index.html` 本身，没有打包/压缩步骤。内联时保留了 three.js 的 `@license` / `SPDX-License-Identifier: MIT` 注释与 FXAA 的 NVIDIA 许可全文；已核对线上 Netlify 版本，注释仍在。

## 未使用需额外声明的第三方素材

- **字体**：仅使用系统字体（PingFang SC、Hiragino Sans GB、Microsoft YaHei、system-ui 等），不随项目分发字体文件。
- **贴图 / 模型**：全部由代码程序化生成（地形、树木、石头、鱼、天空、水面），没有外部图片、模型或 base64 内嵌素材。
- **音频**：全部由 Web Audio API 实时合成（振荡器与噪声缓冲），没有音频文件。
- **图标**：界面使用文字与 CSS 绘制，没有图标库。
- **外部接口**：无后端、无 API 调用、无第三方统计或追踪脚本；鱼获记录仅写入浏览器 `localStorage`。

## 许可全文

### three.js — MIT

```text
The MIT License

Copyright 2010-2023 Three.js Authors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```

### FXAA 3.11（NVIDIA）— BSD-3-Clause

以下文本照 `index.html` 内联源码中的原始注释转录：

```text
Copyright (c) 2014-2015, NVIDIA CORPORATION. All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions
are met:
 * Redistributions of source code must retain the above copyright
   notice, this list of conditions and the following disclaimer.
 * Redistributions in binary form must reproduce the above copyright
   notice, this list of conditions and the following disclaimer in the
   documentation and/or other materials provided with the distribution.
 * Neither the name of NVIDIA CORPORATION nor the names of its
   contributors may be used to endorse or promote products derived
   from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS ''AS IS'' AND ANY
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
PURPOSE ARE DISCLAIMED.  IN NO EVENT SHALL THE COPYRIGHT OWNER OR
CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY
OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

## 合规状态汇总

| 状态 | 项目 |
| --- | --- |
| 已合规 | three.js MIT 头注释与 FXAA NVIDIA 许可全文均保留在源码与线上发布物中；无外链资源、无 API key、无个人联系方式、无真实用户数据 |
| 需补充声明 | 本文件与 README 的「第三方组件与许可」小节（已完成）；AGPL-3.0 `LICENSE` 已写入 |
| 必须处理 | 未发现许可不明或来源不可追溯的贴图、模型、音频、字体。若游戏逻辑代码并非本项目作者原创，需要补充原项目来源与许可，否则不要公开发布 |
