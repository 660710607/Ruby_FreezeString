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
จากโค้ด 3 บรรทัดบน ถ้ารันจะพบว่า Output = "Hello World" เนื่องจาก String นั้นยัง mutable by default (ยังแก้ไขค่าได้อยู่)
<pre>s = "Hello"
s << " World"
s.freeze
s << " Peace" </pre>
จากโค้ด 4 บรรทัดบน ถ้ารันจะพบ Error = can't modify frozen String: "Hello World" (FrozenError)
<br>ที่เกิด error ดังกล่าวเพราะว่า เราพยายามแก้ String ที่ถูก freeze ไปแล้ว (.freeze) ซึ่งจะเป็น error ชนิดที่ชื่อว่า FrozenError
<br><br>ซึ่งถ้าอยากแก้ไข อาจทำได้โดยการสร้าง String ใหม่ แล้วแก้แทน
<br><br> -> ตัวอย่างโค้ด
<pre>str = "Hello World"
str.freeze
new_str = str + "!"
puts new_str </pre>
#### จากแหล่งที่มา https://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison#Freezing_a_Ruby_String

<br><br> ส่วนการคืนค่าของ String ที่ Freeze แล้วนั้นสามารถทำได้โดยใช้ -@ กับ +@
<br> ; "-@" จะเป็นการคืนค่า String ที่ Freeze แล้ว
<br> - โดยถ้า freeze แล้วจะคืนตัวเดิม แต่ถ้ายังไม่ freeze จะทำการ freeze แล้วถึงค่อยคืน
<br><br> -> ตัวอย่างโค้ด
<pre>a = "Hello"
b = -a
b << "World" </pre>
โค้ดนี้จะ error บรรทัดที่ 3 เนื่องจาก b นั้นคือออบเจกต์เดียวกับ a แต่ถูก freeze ไว้แล้ว จึงเปลี่ยนค่าไม่ได้ (FrozenError)
<br><br> ; "+@" จะเป็นการคืนค่า String ที่ไม่มีการ freeze
<br> - โดยถ้ายังไม่ถูก freeze จะคืน obj เดิม แต่ถ้า freeze อยู่จะทำการ dup สำเนาใหม่ที่ไม่ froze
<br><br> -> ตัวอย่างโค้ด
<pre>a = "Hello".freeze
b = +a
b << "World"
puts b </pre>
โค้ดนี้ไม่เกิด error เพราะเป็นการเปลี่ยน string ที่ถูกทำให้ไม่ freeze แล้ว
#### จากแหล่งที่มา https://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison#Freezing_a_Ruby_String
<br><br>

## เปรียบเทียบกับภาษา Java/C/Python
# - Java
<br>ในภาษา Java นั้นได้ถูกออกแบบมาให้ obj บางชนิดเป็น immutable อยู่แล้ว (by default) เช่น String
<br> ( Immutable = once it is created, it cannot be changed. )
<pre>String s1 = "knowledge";
String s2 = s1;
s1 = s1.concat(" base");
System.out.println(s1); </pre>
จากโค้ดบนจะ output : knowledge base
<br> ซึ่งเมื่อเรา concat (ต่อสตริง) มันจะสร้างสตริง "knowledge base" และใส่เข้า s1 ซึ่งสตริงเดิม (original) จะยังไม่ถูกเปลี่ยน (The original string remains unchanged.)
#### จาก https://www.geeksforgeeks.org/java/java-string-is-immutable-what-exactly-is-the-meaning/

<br><br> คำว่า "final" เป็น non-access modifier ซึ่งจะใช้เพื่อป้องกันการแก้ไขข้อมูล
<br>ใช้กับตัวแปร = ค่าไม่เปลี่ยน , ใช้กับเมธอด = ไม่สามารถถูกเขียนทับได้ในคลาสลูก , ใช้กับคลาส = สืบทอดไม่ได้ (cannot be extended)
<pre>final String b = "Hello";
b = "Hola";; </pre>
จากบนจะ error : The final local variable b cannot be assigned. It must be blank and not using a compound assignment
<br>เพราะถ้าตัวแปรถูกประกาศเป็น final แล้วจะ กำหนดค่าให้มันได้เพียงครั้งเดียวเท่านั้น
<br>หลังจากนั้นจะเปลี่ยนค่าไม่ได้อีก
#### จาก https://www.geeksforgeeks.org/java/final-keyword-in-java/

# - C
