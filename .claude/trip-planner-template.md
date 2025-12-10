# 旅行规划模板 - 项目指令

## 目的
此模板用于为任何城市创建完整的旅行行程HTML文件（仅中文版），基于首尔行程的结构。

## 何时使用
当用户请求为某个城市创建新的旅行行程时，使用此模板生成包含所有必要部分的结构化HTML文件。

## 重要：只创建中文版
**只创建一个中文版本：**
- `{city}_itinerary_cn.html` - 中文版

**不需要创建英文版**，伴侣可以使用Google翻译查看。
**不要添加语言切换按钮**。

## 需要向用户询问的信息
创建行程前，询问用户：
1. **城市/目的地名称**（中英文）
2. **旅行日期**（开始和结束日期）
3. **住宿地址**（带地图链接）
4. **当地货币**（如 KRW, JPY, USD）
5. **旅行人数**
6. **任何特定活动或偏好**

## HTML结构模板

### 1. 标题部分
- **标题**：城市名 旅行行程
- **旅行时长和日期**（中文格式）
- **货币汇率**：当地货币 → 人民币 → 瑞典克朗
- **只有主页按钮**（左上角🏠主页）

### 2. 住宿信息部分
**必须包含**:
- 🏠 住宿名称
- 📍 完整地址和Google地图链接
- 🔑 入住/退房日期和时间
- 💡 房东推荐（如有）
- 🚇 最近的地铁/公共交通站

**HTML格式**:
```html
<div class="day-card">
    <div class="day-header" onclick="toggleDay('accommodation-content')" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);">
        <span>🏠 住宿信息</span>
        <span class="toggle-icon" id="accommodation-content-icon">▼</span>
    </div>
    <div class="day-content" id="accommodation-content">
        <!-- 住宿详细信息 -->
    </div>
</div>
```

### 3. 每日行程
**每天包含**:
- 日期和星期（中文格式：12月7日 - 星期日）
- 🚇 交通方式和预估费用
- 编号活动（1️⃣, 2️⃣, 3️⃣...）
- 每个活动应该有：
  - 活动名称（中文 + 英文 + 当地语言）
  - 价格：当地货币 → 人民币 → 瑞典克朗
  - 描述和小贴士
  - Google地图链接
  - 时间建议

**状态标记**:
- ✅ 已完成的日子：标题加"已完成"，用绿色提示框标注推荐
- ⚠️ 失望的体验：使用黄色警告框
- 待定的日子：显示为"待安排"或"还未安排"

**景点详情格式（重要！）**:

每个景点使用以下结构：

```html
<h3 style="margin-top: 20px; color: #667eea;">🏯 景点名称（建议逗留时间）<span style="background: #fce4ec; color: #c2185b; padding: 3px 8px; border-radius: 4px; font-size: 0.6em; margin-left: 8px;">🏠 房东推荐</span></h3>

<div style="background: #fff3e0; padding: 20px; border-radius: 10px; margin: 15px 0; border-left: 4px solid #ff9800;">
    <!-- 交通信息 - 始终可见 -->
    <div class="transport" style="background: transparent; padding: 0; border: none; margin-bottom: 12px;">
        <strong>🚶 交通：</strong>从XX步行/乘巴士XX分钟
    </div>

    <!-- 地址链接 - 可点击跳转Google地图 -->
    <div style="font-size: 0.9em; margin-bottom: 15px;">
        <a href="https://maps.app.goo.gl/xxx" target="_blank" class="location-link" style="color: #e65100; font-weight: 500;">
            📍 完整地址
        </a>
    </div>

    <!-- 可折叠的详细信息 -->
    <div class="category-header" onclick="toggleCategory('place-id-content')" style="background: #ffe0b2; border-left: 3px solid #ff9800; padding: 10px 15px; margin: 0;">
        <span style="color: #e65100; font-weight: 500;">📖 了解更多景点信息</span>
        <span class="category-toggle" id="place-id-content-toggle">▼</span>
    </div>
    <div class="category-content" id="place-id-content">
        <div style="background: #ffe0b2; padding: 15px; border-radius: 0 0 8px 8px; border-left: 3px solid #ff9800;">
            <p style="margin: 0; line-height: 1.6; font-size: 0.95em;">
                <strong>特色：</strong>...<br>
                <strong>等级：</strong>...<br>
                <strong>开放：</strong>...<br>
                <strong>门票：</strong>...
            </p>
        </div>
    </div>
</div>
```

**景点格式要点**:
1. **标题**：景点名称（XX分钟）格式，如"东寺 Tō-ji（60分钟）"
2. **交通**：始终显示，不可折叠
3. **地址**：整个地址作为Google Maps链接，可点击
4. **详细信息**：使用"📖 了解更多景点信息"按钮，可折叠
5. **状态保存**：使用localStorage记住折叠状态

**交通选择原则**:
- 如果景点间步行约30分钟左右，优先推荐步行
- 标注"步行30分钟（喜欢走路的话）"或"建议步行"

**HTML格式**:
```html
<div class="day-card">
    <div class="day-header" onclick="toggleDay('day1-content')">
        <span>12月7日 - 星期日（活动主题）✅ 已完成</span>
        <span class="toggle-icon" id="day1-content-icon">▼</span>
    </div>
    <div class="day-content" id="day1-content">
        <!-- 每日活动使用上述景点详情格式 -->
    </div>
</div>
```

### 4. 待体验/待去部分
**必须在Apps部分之前包含**:
- 紫色渐变标题
- 说明这是灵活列表的提示
- 分类活动：
  - 🎎 传统/文化体验
  - 🛍️ 购物与现代景点
  - 🌃 夜生活与娱乐
  - （根据需要添加其他分类）

**HTML格式**:
```html
<div class="day-card">
    <div class="day-header" onclick="toggleDay('to-experience-content')" style="background: linear-gradient(135deg, #9c27b0 0%, #7b1fa2 100%);">
        <span>🎯 待体验/待去景点</span>
        <span class="toggle-icon" id="to-experience-content-icon">▼</span>
    </div>
    <div class="day-content" id="to-experience-content">
        <div class="note" style="background: #f3e5f5; border-left-color: #9c27b0;">
            <strong style="color: #7b1fa2;">💡 关于这个列表：</strong><br>
            这里收集了所有还没去的地方和体验。每天我们可以讨论明天想去哪里，灵活安排行程！
        </div>
        <!-- 分类体验 -->
    </div>
</div>
```

### 5. 推荐应用与交通方式部分
**必须包含**:

#### A. 公共交通卡/系统
- 🚇 交通卡名称和描述
- 💰 价格：
  - 每次进站/单程费用
  - 卡片押金（如适用）
  - 建议充值金额
- 💳 两种使用方式（如适用）：
  - **方式1**：实体卡（购买地点、押金、充值方式、退卡）
  - **方式2**：手机/虚拟卡（如有则推荐）
- ✅ 使用方法（进出站、换乘、优惠）

#### B. 必备应用
推荐4-6个必备应用：
- 💳 交通/运输应用
- 🗺️ 当地导航应用（比Google地图更好）
- 🌐 翻译应用
- 🍜 美食/餐厅发现应用
- 🎫 预订/门票应用（如适用）
- 💳 支付应用（如适用）

**HTML格式**:
```html
<div class="day-card">
    <div class="day-header" onclick="toggleDay('apps-content')" style="background: linear-gradient(135deg, #ff6b6b 0%, #ee5a6f 100%);">
        <span>📱 推荐应用与交通方式</span>
        <span class="toggle-icon" id="apps-content-icon">▼</span>
    </div>
    <div class="day-content" id="apps-content">
        <!-- 交通部分 -->
        <!-- 应用部分 -->
    </div>
</div>
```

### 6. 页脚
```html
<div style="padding: 30px; text-align: center; color: #666; font-size: 0.9em;">
    <p>祝您旅途愉快！🎉</p>
    <p style="margin-top: 10px;">注：价格仅供参考，实际费用可能有所变动</p>
</div>
```

## 样式指南

### 各部分配色方案
- **住宿**：紫色渐变 `#667eea → #764ba2`
- **已完成日子**：绿色强调 `#4caf50`
- **警告/失望**：黄色强调 `#ffc107`
- **待体验**：紫色渐变 `#9c27b0 → #7b1fa2`
- **应用与交通**：红粉渐变 `#ff6b6b → #ee5a6f`
- **交通详情**：绿色背景 `#e8f5e9`

### 活动分类
- **传统/文化**：橙色 `#ff9800`
- **购物/现代**：蓝色 `#2196F3`
- **夜生活/娱乐**：紫色 `#9c27b0`
- **美食/餐饮**：可使用绿色或自定义颜色

### 推荐 vs 不推荐
- ✅ **推荐**：绿色背景 `#e8f5e9`，绿色边框 `#4caf50`
- ⚠️ **不推荐**：黄色背景 `#fff3cd`，黄色边框 `#ffc107`
- 💡 **小贴士**：浅蓝背景 `#e3f2fd`，蓝色边框 `#2196F3`

## 语言要求

### 中文版 (`_cn.html`)
- **所有部分标题**：纯中文（不需要英文）
- **景点/活动名称**：中文 + 英文 + 当地语言（如适用）
  - 示例：国立国乐院 National Gugak Center 국립국악원
  - 示例：景福宫 Gyeongbokgung Palace 경복궁
  - 示例：东大门购物 Dongdaemun Shopping 동대문
- **描述**：纯中文
- **货币**：当地货币 → 人民币 → 瑞典克朗
- **日期**：中文格式（如"12月7日 - 星期日"）
- **不要添加语言切换按钮**

### 多语言命名原则
- 景点名称：中文在前，然后英文，最后当地语言（如与英文不同）
- 当地语言包括但不限于：韩语、日语、泰语、越南语等
- 如果景点有官方多语言名称，尽量使用官方拼写

## 交互功能

### 必需的CSS样式
在`<style>`标签中添加以下类用于可折叠分类：

```css
/* Collapsible category styles */
.category-header {
    padding: 15px 20px;
    border-radius: 10px;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 20px;
    transition: all 0.3s ease;
}

.category-header:hover {
    opacity: 0.9;
    transform: translateX(5px);
}

.category-content {
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.4s ease;
}

.category-content.open {
    max-height: 5000px;
}

.category-toggle {
    font-size: 0.9em;
    transition: transform 0.3s ease;
}

.category-toggle.collapsed {
    transform: rotate(-90deg);
}
```

### 必需的JavaScript函数

在`<script>`标签中添加以下函数：

```javascript
// 日期section的折叠功能
function toggleDay(dayId) {
    const content = document.getElementById(dayId);
    const icon = document.getElementById(dayId + '-icon');

    if (content.classList.contains('open')) {
        content.classList.remove('open');
        icon.classList.add('collapsed');
        localStorage.setItem(dayId, 'closed');
    } else {
        content.classList.add('open');
        icon.classList.remove('collapsed');
        localStorage.setItem(dayId, 'open');
    }
}

// 分类/景点详情的折叠功能
function toggleCategory(categoryId) {
    const content = document.getElementById(categoryId);
    const toggle = document.getElementById(categoryId + '-toggle');

    if (content.classList.contains('open')) {
        content.classList.remove('open');
        toggle.classList.add('collapsed');
        localStorage.setItem(categoryId, 'closed');
    } else {
        content.classList.add('open');
        toggle.classList.remove('collapsed');
        localStorage.setItem(categoryId, 'open');
    }
}

// 页面加载时恢复保存的状态
document.addEventListener('DOMContentLoaded', function() {
    // 恢复日期sections的状态
    const dayContents = document.querySelectorAll('[id$="-content"]:not([id*="category-"])');
    let hasOpenDay = false;

    dayContents.forEach(content => {
        const dayId = content.id;
        const savedState = localStorage.getItem(dayId);
        const icon = document.getElementById(dayId + '-icon');

        if (savedState === 'open') {
            content.classList.add('open');
            if (icon) icon.classList.remove('collapsed');
            hasOpenDay = true;
        } else if (savedState === 'closed') {
            content.classList.remove('open');
            if (icon) icon.classList.add('collapsed');
        }
    });

    // 如果没有保存状态，默认打开第一天
    if (!hasOpenDay && !localStorage.getItem('day1-content')) {
        const firstDay = document.getElementById('day1-content');
        if (firstDay) firstDay.classList.add('open');
    }

    // 恢复分类的状态
    const categoryContents = document.querySelectorAll('.category-content');
    categoryContents.forEach(content => {
        const categoryId = content.id;
        const savedState = localStorage.getItem(categoryId);
        const toggle = document.getElementById(categoryId + '-toggle');

        if (savedState === 'open') {
            content.classList.add('open');
            if (toggle) toggle.classList.remove('collapsed');
        } else if (savedState === 'closed') {
            content.classList.remove('open');
            if (toggle) toggle.classList.add('collapsed');
        }
    });
});
```

所有可折叠部分必须包含：
- 日期sections: `onclick="toggleDay('section-id')"`
- 景点/分类: `onclick="toggleCategory('category-id')"`

以及对应的切换图标ID：`section-id-icon` 或 `category-id-toggle`

## 价格格式
始终以此格式显示价格：
- `₩1,550 ≈ 10 CNY ≈ 6.5 SEK`
- 当地货币 → 人民币 → 瑞典克朗
- 保留合理的小数位数

## 诚实评价的小贴士
当用户完成活动时：
- 对高度推荐的体验使用绿色框
- 对失望的体验使用黄色警告框
- 包含具体细节：好在哪里/不好在哪里、价格、适合谁
- 添加房东推荐（如适用）
- 提供实用建议（时间、预订、避免什么）

## 文件命名规范
- 中文版：`{city-name-english}_itinerary_cn.html`

示例：
- `seoul_itinerary_cn.html`
- `tokyo_itinerary_cn.html`
- `kyoto_itinerary_cn.html`

## 使用示例

当用户说："帮我创建东京的行程"

1. 询问所需信息（日期、住宿、汇率、偏好）
2. 创建**一个**中文版HTML文件使用此模板结构
3. 包含所有必需部分：
   - 标题（只有主页按钮，没有语言切换）
   - 带汇率转换的标题
   - 住宿信息
   - 每日行程（灵活日子标为"待安排"）
   - 待体验部分
   - 应用与交通
   - 页脚
4. 填充东京特定内容（交通系统、应用、活动）
5. 确保所有价格显示 JPY → CNY → SEK 转换
6. 所有描述用中文，景点名称包含中英文及当地语言

## 注意事项
- 始终基于首尔行程示例的结构
- 保持相同的CSS类和样式
- 景点名称要包含多语言（中文+英文+当地语言）
- 包含实用、诚实和详细的信息
- 通过"待体验"部分使行程保持灵活性
- **记住：只创建一个中文版文件**
- **不要添加语言切换按钮**
- 伴侣可以使用Google翻译查看内容
