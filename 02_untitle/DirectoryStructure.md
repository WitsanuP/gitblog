Directory Structure
1. โครงสร้างสำหรับ Conference / Short Paper (ความยาว 4–8 หน้า)
สำหรับเปเปอร์ระดับ Conference ทั่วไป (เช่น งาน IEEE, EUSIPCO) โครงสร้างจะเน้นความเรียบง่าย ไฟล์เนื้อหาทั้งหมดมักรวมอยู่ในไฟล์ `.tex` เดียวหรือแยกแค่อ้างอิงและรูปภาพ:
```
my-paper/
├── main.tex               # เนื้อหาหลักทั้งหมด (ชื่อเรื่อง, ผู้แต่ง, เนื้อหา)
├── references.bib         # ฐานข้อมูลบรรณานุกรม BibTeX
├── IEEEtran.cls           # ไฟล์ template/class ของ IEEE
├── figures/               # โฟลเดอร์เก็บภาพทั้งหมด (PDF, PNG, EPS)
│   ├── system_model.pdf
│   ├── ber_curve.png
│   └── constellation.pdf
└── .gitignore             # ซ่อน auxiliary files ไม่ให้รก Git
```


2. โครงสร้างสำหรับ Journal / Thesis / เอกสารขนาดยาว
เมื่อเอกสารเริ่มยาวเกิน 10 หน้า หรือมีหลายคนร่วมเขียน มักแยกแต่ละ Section ออกเป็นไฟล์ย่อยในโฟลเดอร์ `sections/` แล้วเรียกผ่านคำสั่ง `\input{...}` ใน `main.tex`:
ตัวอย่างการดึงไฟล์ใน `main.tex`:
```
\input{sections/01_introduction}
\input{sections/02_system_model}
\input{sections/03_proposed_method}
```

# addition
`.gitignore`
```
*.aux
*.bbl
*.blg
*.fdb_latexmk
*.fls
*.log
*.out
*.synctex.gz
build/


```
