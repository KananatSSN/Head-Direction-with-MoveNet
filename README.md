# Head-Direction-with-MoveNet

โมเดลนี้ใช้ผลลัพธ์จาก MoveNet ในการคำนวณทิศทางที่คนกำลังมองโดย

1. ใช้ MoveNet detect key point ทั้ง 17 จุดได้แก่ 
KEYPOINT_DICT = {
     'nose':0,
     'left_eye':1,
     'right_eye':2,
     'left_ear':3,
     'right_ear':4,
     'left_shoulder':5,
     'right_shoulder':6,
     'left_elbow':7,
     'right_elbow':8,
     'left_wrist':9,
     'right_wrist':10,
     'left_hip':11,
     'right_hip':12,
     'left_knee':13,
     'right_knee':14,
     'left_ankle':15,
     'right_ankle':16
 }
 โดย output จาก MoveNet จะมีมิติ 6*17*3 คือ [x_coord, y_coord, confident] สำหรับทั้ง 17 จุด สำหรับ 6 คน ใน 1 frame
 
2. ลากลูกศรจากจุดกึ่งกลางระหว่างหูทั้ง 2 ข้างไปยังจมูกเพื่อลากลูกษรทิศทางหน้าคน

3. แปลงพิกัดลูกศรเป็น Polar Coordinates แล้วใช้ทิศทางของลูกษรแบ่งคลาสทิศทางได้เป็น [Up, Down, Left, Right]

4. ใช้พิกัดของหัวไหล่บอกว่าคนกำลังหันหน้าหรือหันหลังให้กล้องโดยถ้าพิกัดหัวไหล่อยู่ถูกลำดับ(พิกัดหัวไหล่ซ้ายอยู่ด้านซ้าย พิกัดหัวไหล่ขวาอยู่ด้านขวา) แปลว่าคนนั้นกำลังหันหลังให้กล้อง จากขั้นตอนนี้จะสามารถแบ่งคลาสทิศทางหน้าคนได้เป็น [Back, Front]
