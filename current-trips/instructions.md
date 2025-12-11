
## 🗓️ 景点安排模板（规划明天/某天的行程）

> **使用说明：** 需要规划行程时，复制以下模板内容，粘贴给AI，AI会按照模板指引帮你规划。

```
【景点安排 - [日期]】

请按以下步骤帮我规划行程：

**第一步：了解需求**
1. 询问我："明天（[日期]）想去哪里？有什么特别的需求或偏好吗？"
   2. 询问我："有没有必须去的景点？或者想避开的类型？"
3. 询问我："计划几点出发？几点需要回到住宿？"
4. 询问我："对交通方式有偏好吗？（比如：尽量步行、优先公共交通等）"

**第二步：从待体验清单选择景点**
5. 打开行程HTML文件中的"🎯 待体验"部分
6. 根据我的需求，从待体验清单中筛选合适的景点和餐厅：
   - 优先考虑"🏠 房东推荐"的地方
   - 注意景点的开放时间和建议游玩时长
   - 考虑地理位置是否顺路
   - 确认门票价格和地址
   - 如果有官网，记录官网链接

**第三步：规划路线**
7. 根据景点的地理位置，按照最优路线排序（减少往返，节省时间）
8. 计算景点之间的交通时间和方式
9. 考虑用餐时间（早餐、午餐、晚餐），优先选择待体验清单中的"🏠 房东推荐"餐厅

**第四步：交通方案**
10. 计算当天所有交通费用：
    - 列出每段交通的单程费用
    - 计算总交通费用
    - 对比日票价格（如果有的话）
    - 推荐：如果买日票更划算，推荐日票；否则推荐单程票

**第五步：生成详细HTML格式行程**
11. 使用与12月10日、11日相同的HTML格式生成行程表
12. 行程表必须包含以下信息：
    - **每个景点**：
      - 景点标题：游玩时长用小时（如"金阁寺（1小时）"、"哲学之道（0.5小时）"）
      - 如果是房东推荐，加标签：`<span style="background: #fce4ec; color: #c2185b; padding: 3px 8px; border-radius: 4px; font-size: 0.6em; margin-left: 8px;">🏠 房东推荐</span>`
      - **外面显示（重要信息）**：
        - **第一站**：显示"🕘 出发时间：XX:XX 从住宿出发"
        - 交通方式和所需时间
        - 地址和地图链接（格式：`https://www.google.com/maps/search/?api=1&query=地址`）
        - **最后一站**：标注"🏠 返回时间：XX:XX 回到住宿"
      - **可折叠部分（详细信息）**：
        - 特色、开放时间、门票费用、电话、官网
        - 如果是房东推荐，添加：`<strong style="color: #c2185b;">⭐ 房东推荐理由：</strong>推荐理由`
        - 小贴士
    - **用餐安排**：
      - 早餐建议（时间、地点、预估费用）
      - 午餐/晚餐推荐（使用可折叠的"🍜 午餐推荐"/"🍜 晚餐推荐"部分）
      - 如果餐厅是房东推荐，添加标签：`<span style="background: #fce4ec; color: #c2185b; padding: 2px 6px; border-radius: 3px; font-size: 0.75em;">🏠 房东推荐</span>`
    - **每日预算总结**：
      - 交通总计
      - 餐饮总计
      - 门票总计
      - 每日总计
      - 人均费用

**第六步：优化建议**
13. 提供优化建议：
    - 时间是否合理？会不会太赶或太松？
    - 有没有可以调整的地方？
    - 需要预订的景点或餐厅

**第七步：确认**
14. 询问我："这个行程安排满意吗？需要调整吗？"
15. 根据反馈进行调整
16. 确认后，将生成的HTML代码插入到行程文件的对应日期位置

---

请开始第一步！
```

### 📋 HTML格式参考模板

生成行程时，使用以下HTML格式（参考12月11日的最新两层折叠格式）：

```html
<!-- Day X -->
<div class="day-card">
    <div class="day-header" onclick="toggleDay('dayX-content')">
        <span>12月XX日 - 星期X（地区 - 景点1 + 景点2）</span>
        <span class="toggle-icon" id="dayX-content-icon">▼</span>
    </div>
    <div class="day-content" id="dayX-content">

        <!-- 早餐建议 -->
        <div class="note" style="background: #fff3e0; border-left-color: #ff9800; margin-bottom: 15px;">
            <strong>🥐 早餐建议：</strong>XX:XX出发前，在住宿附近便利店买点边走边吃<br>
            <strong>💡 推荐：</strong>饭团🍙、三明治🥪、面包🥐、咖啡☕ - 便宜又方便，约¥300-500/人
        </div>

        <!-- 第一站景点 - 两层折叠结构 -->
        <!-- 第一层：点击景点标题展开，显示基本信息 -->
        <div class="category-header" onclick="toggleCategory('attraction-id-main-content')" style="background: #e8eaf6; border-left: 4px solid #3f51b5; padding: 10px 15px; margin: 15px 0 0 0;">
            <h3 style="color: #283593; margin: 0;">🏯 景点名称 英文名 日文名（X小时）<span style="background: #fce4ec; color: #c2185b; padding: 3px 8px; border-radius: 4px; font-size: 0.6em; margin-left: 8px;">🏠 房东推荐</span></h3>
            <span class="category-toggle" id="attraction-id-main-content-toggle">▼</span>
        </div>
        <div class="category-content" id="attraction-id-main-content">
            <div style="background: #e8eaf6; padding: 20px; border-radius: 0 0 10px 10px; border-left: 4px solid #3f51b5;">
                <!-- 基本信息：交通、地址、开放时间、门票 -->
                <div class="transport" style="background: transparent; padding: 0; border: none; margin-bottom: 12px;">
                    <strong>🕘 出发时间：</strong>XX:XX 从住宿出发<br>
                    <strong>🚌 交通：</strong>乘巴士，约X分钟，¥XXX / 步行X分钟
                </div>
                <div style="font-size: 0.9em; margin-bottom: 12px;">
                    <a href="https://www.google.com/maps/search/?api=1&query=地址" target="_blank" class="location-link" style="color: #283593; font-weight: 500;">
                        📍 完整地址
                    </a>
                </div>
                <div style="font-size: 0.9em; margin-bottom: 15px;">
                    <strong>开放：</strong>开放时间<br>
                    <strong>门票：</strong>¥XXX ≈ XX SEK ≈ XX CNY / 免费 ✨
                </div>

                <!-- 第二层：点击"了解更多"展开详细信息 -->
                <div class="category-header" onclick="toggleCategory('place-id-detail')" style="background: #c5cae9; border-left: 3px solid #3f51b5; padding: 10px 15px; margin: 0;">
                    <span style="color: #283593; font-weight: 500;">📖 了解更多景点信息</span>
                    <span class="category-toggle" id="place-id-detail-toggle">▼</span>
                </div>
                <div class="category-content" id="place-id-detail">
                    <div style="background: #c5cae9; padding: 15px; border-radius: 0 0 8px 8px; border-left: 3px solid #3f51b5;">
                        <p style="margin: 0; line-height: 1.6; font-size: 0.95em;">
                            <strong>特色：</strong>景点特色<br>
                            <strong>建筑/必看：</strong>建筑特点或必看内容<br>
                            <strong>电话：</strong>电话号码<br>
                            <strong>官网：</strong><a href="网址" target="_blank" style="color: #283593;">网址</a><br>
                            <strong style="color: #c2185b;">⭐ 房东推荐理由：</strong>推荐理由（仅房东推荐时）<br>
                            <strong>💡 小贴士：</strong>实用小贴士
                        </p>
                    </div>
                </div>
            </div>
        </div>

        <!-- 其他景点：同样的两层折叠结构，但交通部分不显示出发时间 -->

        <!-- 午餐（可折叠） -->
        <div class="category-header" onclick="toggleCategory('lunch-id-content')" style="background: #f3e5f5; border-left: 4px solid #9c27b0; padding: 10px 15px; margin: 15px 0 0 0;">
            <h3 style="color: #6a1b9a; margin: 0;">🍽️ 午餐：餐厅名称（1小时）</h3>
            <span class="category-toggle" id="lunch-id-content-toggle">▼</span>
        </div>
        <div class="category-content" id="lunch-id-content">
            <div style="background: #f3e5f5; padding: 20px; border-radius: 0 0 10px 10px; margin: 0 0 15px 0; border-left: 4px solid #9c27b0;">
                <div style="background: white; padding: 15px; border-radius: 8px; border-left: 3px solid #4caf50;">
                    <strong style="color: #6a1b9a;">✅ 实际选择：餐厅名称</strong><br>
                    <span style="font-size: 0.9em; color: #666; line-height: 1.8;">
                        🍜 菜系<br>
                        📍 地址<br>
                        💰 套餐/费用 ¥XXX（2人）<br>
                        🌸 <strong>特色：</strong>餐厅特色<br>
                        ⭐ <strong>体验：</strong>用餐体验
                    </span>
                </div>
            </div>
        </div>

        <!-- 返回住宿 -->
        <h3 style="margin-top: 20px; color: #667eea;">🚌 返回住宿</h3>
        <div class="transport">
            <strong>🚌 返程：</strong>乘巴士返回，约X分钟，¥XXX × 2人<br>
            <strong>⏰ 实际XX:XX到达住宿</strong>
        </div>

        <!-- 每日预算总结 -->
        <div class="total-budget">
            <strong>💰 今日预算总计（2人）：</strong><br>
            交通费：¥XXX<br>
            门票费：¥XXX<br>
            餐饮费：¥XXX<br>
            <strong>总计：¥XXX ≈ XX SEK ≈ XX CNY</strong><br>
            <strong style="font-size: 1.1em; color: #fff59d;">💰 每人平均：XX SEK ≈ XX CNY</strong>
        </div>

    </div>
</div>
```

**重要提示：**
- ✅ **两层折叠结构**：
  - **第一层**：景点标题可折叠，展开显示基本信息（交通、地址、开放时间、门票）
  - **第二层**："了解更多景点信息"可折叠，包含详细介绍（特色、建筑、电话、小贴士等）
- ✅ **游玩时长**：只用0.5小时增量（0.5、1、1.5、2小时），不要用0.75、1.25等
- ✅ **交通信息简化**：
  - 不要写具体路线（如"乘巴士100号/5号至XX站"）
  - 只写：`乘巴士，约X分钟，¥XXX` 或 `步行X分钟`
- ✅ **出发/返回时间**：
  - 第一站显示：`🕘 出发时间：XX:XX 从住宿出发`
  - 其他景点不显示出发时间
  - 返回住宿单独列出，显示到达时间
- ✅ **基本信息层**：交通、地址、开放时间、门票
- ✅ **详细信息层**：特色、建筑/必看、电话、官网、房东推荐理由、小贴士
- ✅ **房东推荐标签**：`<span style="background: #fce4ec; color: #c2185b; padding: 3px 8px; border-radius: 4px; font-size: 0.6em; margin-left: 8px;">🏠 房东推荐</span>`
- ✅ **唯一ID命名**：
  - 主内容：`attraction-name-main-content`
  - 详细信息：`place-name-detail`
  - 午餐/晚餐：`lunch-name-content` / `dinner-name-content`
- ✅ **地图链接格式**：`https://www.google.com/maps/search/?api=1&query=地址`

---

## 📝 今日行程总结模板

> **使用说明：** 每天结束后，复制以下模板内容，粘贴给AI，AI会按照模板指引完成今日总结。

```
【今日行程总结 - [日期]】

请按以下步骤帮我完成今日行程总结：

**第一步：回顾计划**
1. 显示今天（[日期]）的原计划行程
2. 询问我："今天的行程完成情况如何？是否按计划完成？"

**第二步：确认实际行程**
3. 询问我："今天实际去了哪些地方？"
4. 对于每个去过的地方，询问：
   - 是否有变化或需要补充的信息

**第三步：收集费用信息**
5. 询问我以下具体费用（请一项一项问）：

   **🚇 交通费用：**
   - 使用的交通方式（地铁/巴士/出租车/日票等）
   - 实际交通花费

   **🍽️ 餐饮费用：**
   - 早餐：在哪里吃的？花费多少？
   - 午餐：在哪里吃的？花费多少？
   - 晚餐：在哪里吃的？花费多少？
   - 其他小吃/饮料：在哪里买的？花费多少？

   **🎫 景点门票费用：**
   - 每个景点的实际门票价格

**第四步：更新行程文件**
6. 将实际基本费用（除购物）更新到行程计划文件中：
   - 在对应景点下标注实际花费
   - 更新每日总支出

**第五步：从待体验清单移除**
7. 将今天去过的地方从"待体验"清单中移除，把今天的行程标记为"✅"， 放在今天行程的首位

**第六步：生成今日消费总结**
8. 生成今日消费总结表格，包含：
   - 交通总计
   - 餐饮总计
   - 门票总计
   - 今日总计
   - 人均费用

**第七步：经验记录**
9. 询问我："有什么想要记录的经验或建议吗？（比如：某个餐厅特别好吃、某个景点建议游玩时长、交通小贴士等）"
10. 将这些经验添加到对应位置作为💡小贴士

---

```

---

## 使用示例

**规划行程时：**
- 复制"景点安排模板"，将 `[日期]` 替换为要规划的日期（如：12月12日）
- 发送给AI，AI会一步步询问需求并帮你规划详细行程

**每天结束后：**
- 复制"今日行程总结模板"，将 `[日期]` 替换为当天日期（如：12月11日）
- 发送给AI，AI会引导你完成今日总结并更新行程文件
