# 📝 Freezing a Ruby String

## 1. เนื้อหา
ในภาษา Ruby คำสั่ง `.freeze` ใช้เพื่อทำให้ object (โดยเฉพาะ String) **กลายเป็น immutable**  
หมายความว่าค่าในตัวแปรจะไม่สามารถถูกเปลี่ยนแปลงได้อีกหลังจาก freeze แล้ว  
หากพยายามแก้ไขจะเกิด **RuntimeError** ขึ้น  

**ประโยชน์**
- ป้องกันการแก้ไขค่าที่ไม่ควรเปลี่ยน (เช่น constant string)
- ใช้เพื่อเพิ่มประสิทธิภาพหน่วยความจำ (ลดการสร้าง object ใหม่ซ้ำ ๆ)
- ใช้ในระบบที่ต้องการความปลอดภัยของข้อมูล

---

## 2. ตัวอย่าง (Ruby)

```ruby
str = "Hello Ruby"
str.freeze

puts str         # => "Hello Ruby"

begin
  str << " World"  # พยายามแก้ไข
rescue => e
  puts e.message   # => "can't modify frozen String"
end
