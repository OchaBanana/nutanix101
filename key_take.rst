.. _key_take:

Takeaways
*********

อะไรบ้างที่เป็นสิ่งสำคัญที่เราควรจะรู้ไว้เกี่ยวกับ Nutanix AOS, Prism, and AHV
 - Prism Element เป็นหน้าจัดการ VM ต่างๆ ของ Nutanix ที่ทำงานอยู่บนทุกๆ node ใน cluster และใช้ผ่านหน้าเวป interface ที่รองรับ HTML5 
 - Prism Element เป็นหน้า interface ที่มีการจัดเตรียมนำข้อมูลต่างๆ ที่มีความสำคัญใน cluster ออกมาแสดงให้ทางผู้ดูแลระบบได้รับทราบ
 - ฟังก์ชัน Distributed Storage Fabric ได้มีการจัดเก็บในส่วนของข้อมูลในรูปแบบ RF2 (เก็บข้อมูล 2 ชุด)หรือ RF3 (เก็บข้อมูล 3 ชุด) กระจายทั่ว shared storage ใน cluster
 - การทำ snapshot ในระดับ VM และการกำหนด replication policy สามารถจัดการกำหนดผ่าน Prism สำหรับ hypervisor ที่รองรับได้
 - เราสามารถกำหนด Storage policy สำหรับ VM ต่างๆ ได้ อย่างเช่น RF level, compression, deduplication และ erasure coding โดยกำหนดผ่าน Storage Container
 - บน AHV ได้ให้ความสามารถของ distributed virtual switching และ IP address management มาด้วย ซึ่งจะช่วยให้การจัดการ virtual network ได้อย่างง่าย
 - บน AHV เราสามารถจัดการ VM ต่างๆ ผ่าน Prism, CLI, หรือ REST API
 - บน AHV ฟังค์ชัน Image Service สามารถให้เราทำ catalog ของ images ที่มีอยู่นั้น เพื่อนำมาใช้ในการทำ VM deployment
 - AHV ได้ให้ฟีเจอร์ที่มีความสำคัญอย่างมากมาด้วย อย่างเช่น live migration, high availability และ dynamic VM placement โดยที่ไม่ต้อง configure ใดๆ เพิ่มเติม
 - สำหรับข้อมูลเพิ่มเติมในส่วนของรายละเอียดของสถาปัตยกรรมของ Nutanix สามารถเข้ามาศึกษาเพิ่มได้จากในนี้ `The Nutanix Bible <https://nutanixbible.com>`_