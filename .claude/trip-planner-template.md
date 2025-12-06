# Trip Planner Template - Project Instructions

## Purpose
This template helps create comprehensive travel itinerary HTML files for any city, based on the Seoul itinerary structure.

## When to Use
When the user requests to create a new trip itinerary for a city, use this template to generate a well-structured HTML file with all necessary sections.

## Required Information from User
Before creating the itinerary, ask the user for:
1. **City/Destination name** (Chinese & English)
2. **Travel dates** (start and end date)
3. **Accommodation address** (with map link)
4. **Local currency** (e.g., KRW, JPY, USD)
5. **Number of travelers**
6. **Any specific activities or preferences**

## HTML Structure Template

### 1. Header Section
- **Title**: City name in both Chinese and English
- **Trip duration and dates**
- **Currency exchange rates**:
  - Local currency → CNY (人民币)
  - Local currency → SEK (瑞典克朗)
  - Format: `1 [Currency] = X CNY ≈ Y SEK`
  - Always show conversion for both CNY and SEK

### 2. Accommodation Section (住宿信息)
**Must include**:
- 🏠 Accommodation name
- 📍 Full address with Google Maps link
- 🔑 Check-in/Check-out dates and times
- 💡 Host recommendations (if available)
- 🚇 Nearest subway/public transport stations

**HTML Format**:
```html
<div class="day-card">
    <div class="day-header" onclick="toggleDay('accommodation-content')" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);">
        <span>🏠 住宿信息 Accommodation</span>
        <span class="toggle-icon" id="accommodation-content-icon">▼</span>
    </div>
    <div class="day-content" id="accommodation-content">
        <!-- Accommodation details -->
    </div>
</div>
```

### 3. Daily Itinerary (每日行程)
**For each day, include**:
- Date with day of week (Chinese & English)
- 🚇 Transportation method and estimated costs
- Numbered activities (1️⃣, 2️⃣, 3️⃣...)
- Each activity should have:
  - Activity name (Chinese & English)
  - Price in local currency → CNY → SEK
  - Description and tips
  - Google Maps link
  - Time recommendations

**Status markers**:
- ✅ Completed days: Add "已完成" in header, use green note boxes for recommendations
- ⚠️ Disappointing experiences: Use yellow warning boxes
- Pending days: Show as "待安排" or "还未安排"

**HTML Format**:
```html
<div class="day-card">
    <div class="day-header" onclick="toggleDay('day1-content')">
        <span>Day 1 - Date（Activity themes）✅ 已完成</span>
        <span class="toggle-icon" id="day1-content-icon">▼</span>
    </div>
    <div class="day-content" id="day1-content">
        <!-- Daily activities -->
    </div>
</div>
```

### 4. To Experience Section (待体验/待去)
**Must include before Apps section**:
- Purple gradient header
- Note explaining this is a flexible list
- Categorized activities:
  - 🎎 Traditional/Cultural experiences
  - 🛍️ Shopping & Modern attractions
  - 🌃 Nightlife & Entertainment
  - (Other categories as needed)

**HTML Format**:
```html
<div class="day-card">
    <div class="day-header" onclick="toggleDay('to-experience-content')" style="background: linear-gradient(135deg, #9c27b0 0%, #7b1fa2 100%);">
        <span>🎯 待体验/待去 To Experience</span>
        <span class="toggle-icon" id="to-experience-content-icon">▼</span>
    </div>
    <div class="day-content" id="to-experience-content">
        <div class="note" style="background: #f3e5f5; border-left-color: #9c27b0;">
            <strong style="color: #7b1fa2;">💡 关于这个列表：</strong><br>
            这里收集了所有还没去的地方和体验。每天我们可以讨论明天想去哪里，灵活安排行程！
        </div>
        <!-- Categorized experiences -->
    </div>
</div>
```

### 5. Apps & Transportation Section (推荐应用与交通方式)
**Must include**:

#### A. Public Transportation Card/System
- 🚇 Card name and description
- 💰 Pricing:
  - Per-entry/per-trip cost
  - Card deposit (if applicable)
  - Suggested recharge amount
- 💳 Two usage methods (if applicable):
  - **Method 1**: Physical card (purchase location, deposit, recharge, refund)
  - **Method 2**: Mobile/virtual card (recommended if available)
- ✅ How to use (entry/exit, transfers, discounts)

#### B. Essential Apps
Recommend 4-6 essential apps:
- 💳 Transit/transportation app
- 🗺️ Local navigation app (better than Google Maps)
- 🌐 Translation app
- 🍜 Food/restaurant discovery app
- 🎫 Booking/ticket app (if applicable)
- 💳 Payment app (if applicable)

**HTML Format**:
```html
<div class="day-card">
    <div class="day-header" onclick="toggleDay('apps-content')" style="background: linear-gradient(135deg, #ff6b6b 0%, #ee5a6f 100%);">
        <span>📱 推荐应用与交通方式</span>
        <span class="toggle-icon" id="apps-content-icon">▼</span>
    </div>
    <div class="day-content" id="apps-content">
        <!-- Transportation section -->
        <!-- Apps section -->
    </div>
</div>
```

### 6. Footer
```html
<div style="padding: 30px; text-align: center; color: #666; font-size: 0.9em;">
    <p>祝您旅途愉快！🎉</p>
    <p style="margin-top: 10px;">注：价格仅供参考，实际费用可能有所变动</p>
</div>
```

## Styling Guidelines

### Color Schemes by Section Type
- **Accommodation**: Purple gradient `#667eea → #764ba2`
- **Completed days**: Green accents `#4caf50`
- **Warning/Disappointments**: Yellow accents `#ffc107`
- **To Experience**: Purple gradient `#9c27b0 → #7b1fa2`
- **Apps & Transportation**: Red-pink gradient `#ff6b6b → #ee5a6f`
- **Transportation details**: Green background `#e8f5e9`

### Activity Categories
- **Traditional/Cultural**: Orange `#ff9800`
- **Shopping/Modern**: Blue `#2196F3`
- **Nightlife/Entertainment**: Purple `#9c27b0`
- **Food/Dining**: Can use green or custom color

### Recommended vs Not Recommended
- ✅ **Recommended**: Green background `#e8f5e9`, green border `#4caf50`
- ⚠️ **Not recommended**: Yellow background `#fff3cd`, yellow border `#ffc107`
- 💡 **Tips**: Light blue background `#e3f2fd`, blue border `#2196F3`

## Language Requirements
- **All section headers**: Chinese + English
- **Activity names**: Chinese + English
- **Descriptions**: Primarily Chinese, with key English terms in parentheses where helpful
- **Currency**: Always show: Local Currency → CNY → SEK
- **Dates**: Chinese format with English weekday

## Interactive Features
All collapsible sections must include:
```javascript
onclick="toggleDay('section-id')"
```
And corresponding toggle icon with ID: `section-id-icon`

## Price Format
Always display prices in this format:
- `₩1,550 ≈ 10 CNY ≈ 6.5 SEK`
- Local currency → CNY (人民币) → SEK (克朗)
- Round to reasonable decimal places

## Tips for Honest Reviews
When user completes activities:
- Use green boxes for highly recommended experiences
- Use yellow warning boxes for disappointing experiences
- Include specific details: what was good/bad, prices, who it's suitable for
- Add host recommendations when applicable
- Provide practical tips (timing, booking, what to avoid)

## File Naming Convention
`{city-name-english}_itinerary_cn.html`

Example: `seoul_itinerary_cn.html`, `tokyo_itinerary_cn.html`

## Example Usage

When user says: "Help me create an itinerary for Tokyo"

1. Ask for required information (dates, accommodation, currency rate, preferences)
2. Create HTML file using this template structure
3. Include all mandatory sections:
   - Header with currency conversion
   - Accommodation
   - Daily itinerary (with flexible days as "待安排")
   - To Experience section
   - Apps & Transportation
   - Footer
4. Populate with Tokyo-specific content (transit system, apps, activities)
5. Ensure all prices show JPY → CNY → SEK conversion

## Notes
- Always base structure on the Seoul itinerary example
- Keep the same CSS classes and styling
- Maintain bilingual content throughout
- Include practical, honest, and detailed information
- Make the itinerary flexible with "To Experience" section for unplanned days
