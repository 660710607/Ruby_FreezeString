# Freezing a Ruby String

## เนื้อหา
ปกติในภาษา Ruby การแก้ไข String หนึ่งจะสามารถทำได้ทันที (Mutable Object เช่น String , Array , Hash)
<br> แต่ถ้าอยากให้แก้ไขไม่ได้จะต้องทำการ Freeze ใส่ String หรือวัตถุนั้นๆ
<br><br> - โดยเราจะต้องใช้คำสั่ง .freeze กับ String หรือ Object ใดๆ 
<br> - จะเหมือนเป็นการล็อก String นั้นไว้ ไม่ให้แก้ค่าได้
<br><br> -> ตัวอย่างโค้ด
<pre>s = "Hello"
s << " World"
puts s </pre>
ถ้ารันโค้ด 3 บรรทัดข้างบน จะพบว่า Output = "Hello World" เนื่องจาก String นั้นยัง mutable by default (ยังแก้ไขค่าได้อยู่)
<pre>s = "Hello"
s << " World"
s.freeze
s << " Peace" </pre>
แต่ถ้ารันโค้ด 4 บรรทัดข้างบน จะพบว่า Error = can't modify frozen String: "Hello World" (FrozenError)
ที่เกิด error ดังกล่าวเพราะว่า เราพยายามแก้ String ที่ถูก freeze ไปแล้ว (.freeze) ซึ่งจะเป็น error ชนิดที่ชื่อว่า "FrozenError)
ซึ่งถ้าอยากแก้ไข จะต้องสร้าง String ใหม่ แล้วแก้แทน
<br><br> -> ตัวอย่างโค้ด
<pre> str = "Hello World"
str.freeze
new_str = str + "!"
puts new_str </pre>
