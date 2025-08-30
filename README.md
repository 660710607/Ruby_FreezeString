# Freezing a Ruby String

## / เนื้อหา
ปกติในภาษา Ruby การแก้ไข String หนึ่งจะสามารถทำได้ทันที (Mutable Object เช่น String , Array , Hash)
<br> แต่ถ้าอยากให้แก้ไขไม่ได้จะต้องทำการ Freeze ใส่ String หรือวัตถุนั้นๆ
<br> - โดยเราจะต้องใช้คำสั่ง .freeze กับ String หรือ Object ใดๆ 
<br> - จะเหมือนเป็นการล็อก String นั้นไว้ ไม่ให้แก้ค่าได้
