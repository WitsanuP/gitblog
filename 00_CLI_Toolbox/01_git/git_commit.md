# 📝 Git Commit Guidelines & Best Practices

คู่มือและแนวทางการเขียน Git Commit Message ให้เป็นระเบียบ อ่านเข้าใจง่าย และเป็นไปตามมาตรฐานสากล (**Conventional Commits Specification**)

---

## 📌 โครงสร้างพื้นฐาน (Commit Structure)

```text
<type>(<scope>): <subject>

[body] (optional)

[footer] (optional)
```

- **Type**: ประเภทของการเปลี่ยนแปลง (จำเป็นต้องระบุ)
- **Scope**: ขอบเขตหรือโมดูลที่ได้รับผลกระทบ เช่น `(auth)`, `(api)`, `(ui)` (ระบุหรือไม่ก็ได้)
- **Subject**: คำอธิบายสั้นๆ เกี่ยวกับการเปลี่ยนแปลง (ความยาวไม่เกิน 50 ตัวอักษร)
- **Body**: รายละเอียดเพิ่มเติม อธิบายว่าทำไมถึงต้องแก้ และแก้อย่างไร (เว้น 1 บรรทัดจาก Subject)
- **Footer**: อ้างอิง Issue หรือแจ้งการเปลี่ยนแปลงครั้งใหญ่ (Breaking Changes) เช่น `Closes #123`

---

## 🏷️ ประเภทของ Commit (Types)

| Type | ความหมาย | ตัวอย่าง |
| :--- | :--- | :--- |
| **`feat`** | เพิ่มฟีเจอร์ใหม่ (Feature) | `feat(auth): add google oauth login` |
| **`fix`** | แก้ไขข้อผิดพลาด (Bug Fix) | `fix(cart): resolve negative quantity calculation` |
| **`refactor`** | ปรับปรุงโครงสร้างโค้ด โดยไม่กระทบฟังก์ชันการทำงาน | `refactor(parser): simplify token iteration logic` |
| **`perf`** | ปรับปรุงประสิทธิภาพ (Performance Improvement) | `perf(query): add index to user email column` |
| **`docs`** | แก้ไขหรือเพิ่มเอกสารประกอบ (Documentation) | `docs: update setup and installation guide` |
| **`style`** | จัดรูปแบบโค้ด, formatting, semicolon (ไม่มีผลต่อ logic) | `style: apply prettier format across src/` |
| **`test`** | เพิ่มหรือแก้ไข Unit / Integration Test | `test(auth): add test cases for expired JWT` |
| **`chore`** | งานเบ็ดเตล็ด เช่น อัปเดต dependencies, config build | `chore: upgrade tailwindcss to v4.0` |
| **`ci`** | ปรับแต่ง CI/CD pipelines (GitHub Actions, GitLab CI) | `ci: add automated lint and test workflows` |
| **`build`** | การเปลี่ยนแปลงเกี่ยวกับระบบ build หรือ external dependencies | `build: configure vite alias for assets` |

---

## ⚡ กฎทอง 4 ข้อสำหรับการเขียน Subject

1. **ใช้คำกริยาเชิงสั่ง (Imperative Mood):**  
   - ✅ `Add user logout endpoint`  
   - ❌ `Added user logout endpoint`  
   - ❌ `Adding user logout endpoint`  
2. **ไม่ใส่เครื่องหมายจุด (`.`) ปิดท้ายประโยค**
3. **ใช้ตัวพิมพ์เล็กสม่ำเสมอ** (ยกเว้นชื่อเฉพาะหรือคำย่อ)
4. **ความยาวกระชับ:** ไม่ควรเกิน 50 ตัวอักษร

---

## 💡 ตัวอย่างการเขียน Commit

### 1. แบบบรรทัดเดียว (Single-line Commit)
```bash
git commit -m "feat(profile): allow users to upload custom avatars"
```

### 2. แบบหลายบรรทัดพร้อมรายละเอียด (Multi-line Commit)
```bash
git commit -m "fix(checkout): prevent duplicate payment submissions

Disable the submit button immediately upon the first click to avoid 
race conditions during high network latency.

Closes #412"
```

### 3. แจ้งการเปลี่ยนแปลงครั้งใหญ่ (Breaking Changes)
```bash
git commit -m "feat(api)!: migrate auth endpoints to v2

BREAKING CHANGE: The \`/api/v1/login\` route has been deprecated and replaced with \`/api/v2/auth/token\`."
```

---

## 🎯 Best Practices เพิ่มเติม

- **Atomic Commits:** แยก Commit ให้เล็กและทำงานเรื่องเดียว (One task per commit) เพื่อให้ง่ายต่อการ Revert หรือ Code Review
- **Why > How:** โค้ดบอกวิธีทำอยู่แล้ว Commit Message ควรอธิบาย "เหตุผล (Why)" ที่ต้องเปลี่ยนแปลง
