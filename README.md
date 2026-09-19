# <ชื่อทีม>-swreqspec

repo สำหรับงาน Spec-Driven Development ในรายวิชา 520461-165 Software Requirement Specification and Management
ภาควิชาคอมพิวเตอร์ คณะวิทยาศาสตร์ มหาวิทยาลัยศิลปากร

## ทีม

- ชื่อทีม:
- สมาชิก:
- เครื่องมือ AI ที่ใช้: (Copilot ใน Codespaces / Claude Code / Cursor)

## โครงของ repo

```
README.md                    ไฟล์นี้ (ใส่ชื่อทีม สมาชิก และ reflection ท้ายคาบ)
AGENTS.md                    กติกาที่ AI ต้องทำตาม (Copilot และ Cursor อ่านเอง)
CLAUDE.md                    ชี้ไป AGENTS.md (สำหรับ Claude Code)
docs/srs/                    SRS ฉบับเต็มและ diagram ของทีม (สำหรับคนอ่าน)
specs/README.md              ดัชนีว่าฟีเจอร์ไหนอยู่โฟลเดอร์ไหน
specs/001-booking/spec.md    ตัวอย่าง spec.md ของรายวิชา (ใช้ฝึกในคาบ)
specs/00N-<feature>/spec.md  spec.md ของทีม 1 โฟลเดอร์ต่อ 1 ฟีเจอร์
prompt-log.md                AI สร้างให้เมื่อใช้ /clarify (บันทึกคำถามและคำตอบ)
.github/prompts/             คำสั่ง /clarify และ /plan สำหรับ Copilot
.claude/commands/            คำสั่ง /clarify และ /plan สำหรับ Claude Code
.cursor/commands/            คำสั่ง /clarify และ /plan สำหรับ Cursor
```

## วิธีเริ่ม

1. กด Code แล้วเลือก Codespaces สร้างเครื่องใหม่ (หรือ clone ลงเครื่องแล้วเปิดด้วย Cursor / Claude Code)
2. เปิด Copilot Chat สลับเป็นโหมด Agent
3. พิมพ์ `/clarify specs/001-booking/spec.md`
4. ตอบคำถาม แล้วดู diff ของ spec.md ก่อน commit

รายละเอียดคำสั่งอยู่ที่ `docs/agent-pack-README.md`

## ถ้าเป็น repo ของทีม

- แก้ชื่อ repo เป็น `<ชื่อทีม>-swreqspec` และตั้งเป็น public
- ลบโฟลเดอร์ `specs/001-booking/` แล้วสร้าง `specs/001-<ชื่อฟีเจอร์ของทีม>/spec.md`
- อัปโหลด SRS และ diagram ของทีมไว้ที่ `docs/srs/`

## Reflection: 

### UC-01 บันทึกข้อมูลสถานที่และชุมชน
1. ในช่วงแรกพบปัญหาข้อจำกัดของ AI ใน Codespaces ทำให้ต้องปรับกระบวนการทำงานมาวิเคราะห์และเคลียร์ความกำกวมผ่าน Prompt Engineering ร่วมกับ Gemini แทน
2. คำถามจากกระบวนการ `/clarify` ช่วยชี้ให้เห็นจุดอ้ำอึ้งสำคัญในระบบ เช่น เรื่องสิทธิ์การแก้ไขข้อมูลข้ามค่าย และเงื่อนไขการบันทึกเอกสารแนบ
3. การตอบคำถามโดยระบุข้อสันนิษฐาน (Assumptions) และข้อสงสัย (Open Questions) ช่วยให้ขอบเขตของ Requirement มีความชัดเจนขึ้นอย่างเป็นรูปธรรม
4. การรันกระบวนการ `/plan` ช่วยแปลงความต้องการใน spec.md ให้กลายเป็นโครงสร้าง Data Models, API Components และ Constraints Checklist ที่พร้อมนำไปพัฒนาจริง
5. การทำงานร่วมกับ AI ทำให้เห็นความสำคัญของการทบทวนและบันทึกประวัติการตัดสินใจ (prompt-log) ซึ่งช่วยให้ทีมพัฒนาระบบมีความเข้าใจตรงกันและลดความผิดพลาดในการโค้ดดิ้ง

### UC-07 พิจารณาและอนุมัติโครงการ
1. กระบวนการ `/clarify` ช่วยชี้ให้เห็นจุดอ้ำอึ้งสำคัญในกระบวนการอนุมัติ เช่น รูปแบบของลายมือชื่อดิจิทัล และขอบเขตของ Acceptance Criteria ที่ต้องปรับให้สอดคล้องกับ Use Case จริง
2. การกำหนดเงื่อนไขการยืนยันตัวตนผ่าน Login Session (`ASM-07-01`) ช่วยลดความซับซ้อนในขั้นตอนการออกแบบระบบลงได้มาก
3. การระบุกระบวนการส่งกลับแก้ไขและส่งซ้ำ (`ASM-07-02`) ทำให้ได้ State Flow ของการพิจารณาโครงการที่ชัดเจนและครอบคลุมทั้ง Happy Path และ Exception Path
4. การทำ `/plan` ช่วยแปลงกระบวนการอนุมัติเอกสารให้กลายเป็น Data Models (Project Approval & History) และ Checklist สำหรับระบบแจ้งเตือนที่พร้อมนำไปโค้ดดิ้งต่อ

