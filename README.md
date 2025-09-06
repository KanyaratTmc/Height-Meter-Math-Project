# โปรเจคคณิตศาสตร์: การประยุกต์ใช้ฟังก์ชันตรีโกณมิติ (PWA)

🏆 **โครงงานคณิตศาสตร์ระดับม.ปลาย** - การประยุกต์ใช้ฟังก์ชันตรีโกณมิติในการวัดความยาว พื้นที่ และความสูง

⚡ วัดระยะ วัดพื้นที่ วัดความสูง และวัดมุม ผ่านกล้องบนเว็บ พร้อมแสดงสูตรคณิตศาสตร์และขั้นตอนการคำนวณ

## 🧮 ฟีเจอร์ทางคณิตศาสตร์
- 📐 **ฟังก์ชันตรีโกณมิติ**: sin, cos, tan, arctan
- 📊 **แสดงสูตรและขั้นตอนการคำนวณ** แบบละเอียด
- 🔢 **ทฤษฎีบทพีทาโกรัส** สำหรับการคำนวณความยาว
- 📏 **Shoelace Formula** สำหรับการคำนวณพื้นที่
- 📐 **การคำนวณมุม** ด้วยฟังก์ชัน arctan

## 🎯 ฟีเจอร์การใช้งาน
- 🎥 เลือกกล้องอัตโนมัติ (ซ่อน UI เพื่อความเรียบง่าย)
- 👆 แตะเพื่อวางจุด พร้อมปุ่ม Undo
- 📐 โหมด: วัดความยาว, วัดพื้นที่, วัดความสูง, **วัดมุม (ตรีโกณมิติ)**
- 🎯 คาลิเบรตแม่นยำ: อัตโนมัติด้วยวัตถุอ้างอิง หรือแบบกำหนดเอง
- 💾 บันทึกสเกลไว้ใน localStorage
- 📏 แสดงไม้บรรทัดพร้อม tick (0 ม., 0.5 ม., 1 ม.)
- 📴 รองรับออฟไลน์ด้วย Service Worker และหน้า offline

## สารบัญ
- ฟีเจอร์ทางคณิตศาสตร์
- ฟีเจอร์การใช้งาน
- การปรับปรุงล่าสุด
- เดโม่
- วิธีใช้งาน
- คาลิเบรต
- ไม้บรรทัดสเกล
- ออฟไลน์ (PWA)
- สูตรคณิตศาสตร์ที่ใช้
- ข้อจำกัดการใช้งาน
- พัฒนา
- การ Deploy
- ความเป็นส่วนตัวและสิทธิ์
- License

## เดโม่
เพิ่มภาพหน้าจอหรือ GIF ตัวอย่าง

![ภาพหน้าจอ](./docs/demo1.png)
![ตัวอย่าง GIF](./docs/demo.gif)

## วิธีใช้งานสำหรับการแข่งขันคณิตศาสตร์
1. เปิด `index.html` ผ่าน HTTPS (หรือใช้เซิร์ฟเวอร์ในเครื่อง)
2. กดปุ่มเปิดกล้อง
3. **ศึกษาสูตรคณิตศาสตร์** ที่แสดงในส่วนบนของแอป
4. เลือกโหมดการวัด:
   - **วัดความยาว**: ใช้ทฤษฎีบทพีทาโกรัส + Advanced Perspective Correction
   - **วัดพื้นที่**: ใช้ Shoelace Formula
   - **วัดความสูง**: ใช้เครื่องคิดเลขกฎของโคไซน์ (ไม่ต้องใช้กล้อง)
   - **วัดมุม**: ใช้ฟังก์ชัน arctan
5. สำหรับโหมดความสูง: ใส่ค่ามุม C และด้าน a, b ในช่องอินพุต
6. สำหรับโหมดอื่น: แตะบนวิดีโอเพื่อเพิ่มจุดตามโหมดที่เลือก
7. กด **"คำนวณ"** เพื่อดูผลลัพธ์และ**ขั้นตอนการคำนวณแบบละเอียด**

## คาลิเบรตแม่นยำ
### คาลิเบรตอัตโนมัติ (แนะนำ)
- กดปุ่ม **"คาลิเบรตอัตโนมัติ"**
- เลือกวัตถุอ้างอิง: บัตรเครดิต, กระดาษ A4, เหรียญ 10 บาท, มือถือ, ปากกา
- แตะ 2 จุดที่ขอบของวัตถุ - ระบบจะคำนวณสเกลอัตโนมัติ

### คาลิเบรตแบบกำหนดเอง
- เปิดโหมดคาลิเบรต แตะสองจุดที่รู้ระยะจริง ใส่ค่าระยะ (เมตร)
- แอปจะคำนวณ px/เมตร และบันทึกลง localStorage อัตโนมัติ

## ไม้บรรทัดสเกล
- แสดงที่มุมซ้ายล่างของหน้ากล้อง
- มี tick ที่ 0 ม., 0.5 ม., 1 ม. ตามพื้นที่ที่มี
- อัปเดตเมื่อสเกลเปลี่ยน หลังคาลิเบรต ตอนโหลดหน้า และเมื่อปรับขนาดหน้าต่าง

## ออฟไลน์ (PWA)
- `sw.js` แคชไฟล์สำคัญ และแสดง `offline.html` เมื่อออฟไลน์
- `manifest.json` กำหนดข้อมูลติดตั้งและไอคอน
- รองรับการติดตั้งเป็นแอปบนมือถือและเดสก์ท็อป

## สูตรคณิตศาสตร์ที่ใช้
1. **ทฤษฎีบทพีทาโกรัส**: c² = a² + b²
2. **ฟังก์ชัน Sine**: sin θ = ตรงข้าม / ด้านตรงข้ามมุมฉาก
3. **ฟังก์ชัน Cosine**: cos θ = ประชิด / ด้านตรงข้ามมุมฉาก
4. **ฟังก์ชัน Tangent**: tan θ = ตรงข้าม / ประชิด
5. **ฟังก์ชัน Arctangent**: θ = arctan(ตรงข้าม / ประชิด)
6. **Shoelace Formula**: Area = ½|∑(xᵢyᵢ₊₁ - xᵢ₊₁yᵢ)|

## ข้อจำกัดการใช้งาน
### 📏 โหมดวัดความยาว
**ข้อจำกัดสำคัญ:**
- ✅ **ต้องเล็งตั้งฉากกับวัตถุเท่านั้น** - วัตถุต้องอยู่ในระนาบเดียวกับกล้อง
- ✅ **ต้องตั้งกล้องให้ตั้งฉากกับพื้น** - ใช้โหมดตั้งฉาก (Perpendicular Mode) เพื่อความแม่นยำ
- ⚠️ **ระยะวัตถุเปลี่ยน ต้อง calibrate ทุกครั้ง** - สเกลขึ้นอยู่กับระยะห่างจากกล้อง
- 📐 **ใช้ได้ดีกับวัตถุเรียบ เช่น ผนัง โต๊ะ พื้น** 
- 🎯 **ระยะที่แนะนำ: 0.5-5 เมตร** - นอกเหนือจากนี้ความแม่นยำลดลง
- 💡 **ต้องมีแสงเพียงพอ** - แสงน้อยทำให้ตรวจจับจุดไม่ชัดเจน

### 📐 โหมดวัดพื้นที่
**ข้อจำกัดสำคัญ:**
- ✅ **วัตถุต้องอยู่บนพื้นราบเท่านั้น** - ไม่สามารถวัดพื้นผิวโค้งหรือเอียงได้
- ✅ **ต้องตั้งกล้องให้ตั้งฉากกับพื้นผิวที่วัด** - มุมเอียงจะทำให้ผลลัพธ์ผิดพลาด
- 📏 **ต้องมีอย่างน้อย 3 จุด** - สำหรับสร้างรูปหลายเหลี่ยม
- 🔄 **ต้องวางจุดตามลำดับรอบรูป** - ไม่ควรวางจุดข้ามกัน
- 🎯 **เหมาะกับพื้นที่ขนาด 1-20 ตารางเมตร** 
- ⚠️ **ระยะห่างจากกล้องต้องคงที่** - วัตถุทุกจุดควรอยู่ระยะเท่ากัน
- 💡 **ไม่เหมาะกับพื้นผิวสะท้อนแสง** เช่น กระจก น้า

### 📏 โหมดวัดความสูง  
**ข้อจำกัดสำคัญ:**
- ✅ **ต้องใช้โหมดตั้งฉาก (Perpendicular Mode)** - กล้องต้องตั้งฉากกับพื้น (มุม 0°)
- 📐 **วัตถุต้องตั้งตรงแนวตั้ง** - เสาธง ต้นไม้ อาคาร คน
- 🎯 **ต้องตั้งค่าความสูงกล้องให้ถูกต้อง** (0.5-3.0 เมตร)
- ⚠️ **ระยะห่างจากวัตถุมีผลต่อความแม่นยำ** - ใกล้เกินไป (< 2 เมตร) หรือไกลเกินไป (> 10 เมตร) จะคลาดเคลื่อน
- 📏 **วัตถุต้องมองเห็นจุดฐานและจุดยอดชัดเจน**
- 🌤️ **ต้องมีแสงเพียงพอและไม่มีเงาบดบัง**
- 💡 **ไม่เหมาะกับวัตถุโปร่งใส หรือมีสีเข้มมาก**

### 📐 โหมดวัดมุม (ตรีโกณมิติ)
**ข้อจำกัดสำคัญ:**
- ✅ **ต้องมี 3 จุดที่ชัดเจน** - จุดยอดมุมและ 2 จุดปลาย
- 📐 **วัตถุทั้ง 3 จุดต้องอยู่ในระนาบเดียวกัน** 
- 🎯 **จุดยอดมุมต้องวางเป็นจุดแรก** - ลำดับการวางจุดสำคัญ
- ⚠️ **มุมที่วัดได้: 5°-175°** - มุมแหลมมากหรือป้านมากจะไม่แม่นยำ
- 📏 **ระยะห่างระหว่างจุดต้องเหมาะสม** - ไม่ใกล้หรือไกลเกินไป
- 💡 **เหมาะกับการวัดมุมของอาคาร เฟอร์นิเจอร์ หรือวัตถุที่มีขอบชัดเจน**

### 🔧 ข้อจำกัดทั่วไปของระบบ
**ปัจจัยที่ส่งผลต่อความแม่นยำ:**
- 🌐 **FOV (Field of View)** - ขึ้นอยู่กับอุปกรณ์และการตั้งค่า
- 📱 **ประเภทอุปกรณ์** - มือถือ แท็บเล็ต เดสก์ท็อป มีค่า FOV ต่างกัน
- 🔄 **การหมุนหน้าจอ** - Portrait/Landscape ส่งผลต่อการคำนวณ
- 💡 **แสงและเงา** - แสงไม่เพียงพอหรือเงาบดบังจะลดความแม่นยำ
- 🤳 **ความคงที่ของมือ** - การสั่นไหวของกล้องส่งผลต่อผลลัพธ์
- 📐 **ระยะห่างที่เหมาะสม** - แต่ละโหมดมีระยะที่เหมาะสมต่างกัน

### 💡 คำแนะนำเพื่อความแม่นยำสูงสุด
1. **ใช้โหมดตั้งฉาก** เมื่อเป็นไปได้
2. **คาลิเบรตก่อนการวัดทุกครั้ง** โดยใช้วัตถุอ้างอิงที่รู้ขนาดแน่นอน
3. **ตั้งค่าความสูงกล้องให้ถูกต้อง** ตามการถืออุปกรณ์จริง
4. **วัดในสภาพแสงเพียงพอ** หลีกเลี่ยงแสงแรงหรือเงาบดบัง
5. **ถือกล้องให้มั่นคง** หลีกเลี่ยงการสั่นไหว
6. **เลือกระยะห่างที่เหมาะสม** ตามโหมดที่ใช้งาน

## พัฒนา
- โค้ดเป็น HTML/CSS/JS ล้วน ไม่มีขั้นตอน build
- ไฟล์สำคัญ:
  - `index.html` – UI สมัยใหม่, กล้อง, คำนวณการวัด, สูตรคณิตศาสตร์, คาลิเบรต
  - `sw.js` – จัดการแคชและออฟไลน์
  - `manifest.json` – ข้อมูล PWA
  - `offline.html` – หน้าออฟไลน์
  - `icons/` – ไอคอน PWA

### เทคโนโลยีที่ใช้
- **Frontend**: HTML5, CSS3 (Glassmorphism), Vanilla JavaScript
- **Camera API**: MediaDevices.getUserMedia()
- **Device Detection**: User Agent parsing และ MediaStreamTrack API
- **Responsive Design**: CSS Grid, Flexbox, Media Queries
- **Animations**: CSS Transitions และ Keyframes
- **PWA**: Service Worker, Web App Manifest

## การ Deploy
- แนะนำ Firebase Hosting (ต้องมีโปรเจกต์ของคุณเอง)
- หรือใช้โฮสต์ static ใด ๆ ที่รองรับ HTTPS (Netlify, GitHub Pages ฯลฯ)
- ต้องใช้ HTTPS เพื่อเข้าถึงกล้อง

## ความเป็นส่วนตัวและสิทธิ์
- กล้องถูกใช้งานภายในเบราว์เซอร์บนอุปกรณ์ของผู้ใช้เท่านั้น
- ไม่ใช้บริการภายนอกหรือไลบรารีเสริม
- ไม่มีการส่งข้อมูลออกจากอุปกรณ์
- ข้อมูลการคาลิเบรตเก็บใน localStorage เท่านั้น

## Roadmap
- ✅ เครื่องคิดเลขกฎของโคไซน์สำหรับโหมดความสูง
- ✅ UI สมัยใหม่พร้อม Glassmorphism
- ✅ ระบบ FOV Detection อัตโนมัติ
- ✅ Advanced Perspective Correction
- 🔄 ปรับปรุงหน้าออฟไลน์ให้มีคำแนะนำ
- 🔄 เพิ่มการแจ้งเตือนการอัปเดต
- 🔄 บันทึกการตั้งค่ากล้องที่ต้องการ

## Contributing
Issues และ PRs ยินดีต้อนรับ สำหรับการเปลี่ยนแปลงใหญ่ กรุณาเปิด issue ก่อนเพื่อหารือ

## License
MIT — ดูไฟล์ `LICENSE`.

Copyright (c) 2025 Kanyarat Thammachot

---
# Height Meter Math (PWA)

⚡ Advanced camera measurement app with modern UI — distance, area, height calculator — featuring Law of Cosines and offline support.

![Status](https://img.shields.io/badge/status-active-brightgreen) ![License](https://img.shields.io/badge/license-MIT-blue) ![PWA](https://img.shields.io/badge/PWA-offline%20ready-ff69b4)

Measure distance, area, and calculate height using Law of Cosines right in your browser. Features modern glassmorphism UI, advanced perspective correction, and works offline (PWA).

- 🎥 Auto camera selection with FOV detection
- 👆 Tap-to-place points + Undo/Clear
- 📐 Modes: Distance, Area (polygon), **Height (Law of Cosines calculator)**, Angle
- 🧮 **Law of Cosines Calculator**: c² = a² + b² - 2ab cos(C)
- 🎯 Advanced calibration with reference objects
- 💾 Scale persists in localStorage
- 📏 Ruler overlay with ticks
- 🎨 Modern glassmorphism UI with responsive design
- 📴 PWA offline support

## Key Features
- **Height Calculator**: Pure mathematical Law of Cosines calculator (no camera required)
- **Advanced Perspective Correction**: Device-specific FOV detection and tilt compensation
- **Modern UI**: Glassmorphism design with smooth animations
- **Responsive Design**: Optimized for mobile, tablet, and desktop
- **Perpendicular Mode**: Enhanced accuracy for measurements
- **Real-time Calculations**: Instant updates as you type

## Getting Started
1. Open `index.html` via HTTPS (or run a local server)
2. Click the camera button to start (except for height mode)
3. **Height Mode**: Use the calculator inputs (angle C, side a, side b)
4. **Other Modes**: Choose a mode and tap to add points
5. Set scale via calibration or manual input
6. Click Calculate to see results and detailed calculation steps

## Privacy & Permissions
- Camera access stays on-device in the browser
- No external services or libraries used
- All calculations performed locally
- Calibration data stored in localStorage only

## License
MIT — see `LICENSE`.

Copyright (c) 2025 Kanyarat Thammachot
