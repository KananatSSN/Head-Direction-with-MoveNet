# Head-Direction-with-MoveNet

โมเดลนี้ใช้ผลลัพธ์จาก MoveNet ในการคำนวณทิศทางที่คนกำลังมองโดย

1. ใช้ MoveNet detect key point ทั้ง 17 จุดได้แก่ [nose, left_eye, right_eye, left_ear, right_ear, left_shoulder, right_shoulder, left_elbow, right_elbow, left_wrist, right_wrist, left_hip, right_hip, left_knee, right_knee, left_ankle, right_ankle]
 โดย output จาก MoveNet จะมีมิติ 6,17,3 คือ [x_coord, y_coord, confident] สำหรับทั้ง 17 จุด สำหรับ 6 คน ใน 1 frame
 
2. ลากลูกศรจากจุดกึ่งกลางระหว่างหูทั้ง 2 ข้างไปยังจมูกเพื่อลากลูกษรทิศทางหน้าคน

3. แปลงพิกัดลูกศรเป็น Polar Coordinates แล้วใช้ทิศทางของลูกษรแบ่งคลาสทิศทางได้เป็น [Up, Down, Left, Right]

4. ใช้พิกัดของหัวไหล่บอกว่าคนกำลังหันหน้าหรือหันหลังให้กล้องโดยถ้าพิกัดหัวไหล่อยู่ถูกลำดับ(พิกัดหัวไหล่ซ้ายอยู่ด้านซ้าย พิกัดหัวไหล่ขวาอยู่ด้านขวา) แปลว่าคนนั้นกำลังหันหลังให้กล้อง จากขั้นตอนนี้จะสามารถแบ่งคลาสทิศทางหน้าคนได้เป็น [Back, Front]
