# 📢 Tìm Hiểu Về **Interrupts** và **Timers** Trong Vi Điều Khiển 🎯

Bạn có biết rằng **Interrupts (Ngắt)** giúp hệ thống nhúng phản ứng nhanh hơn và tiết kiệm tài nguyên CPU hơn so với phương pháp **Polling (Thăm Dò)**? Và **Timers** là công cụ mạnh mẽ giúp tạo độ trễ chính xác, đo thời gian và tạo tín hiệu PWM? Hãy cùng tìm hiểu nhé! 🔥

---

## 🚀 **1. Interrupts – Cách Hoạt Động & Ưu Điểm**

### 🔹 Interrupts là gì?
➡️ Là tín hiệu làm gián đoạn chương trình chính để xử lý một sự kiện quan trọng, sau đó tiếp tục chạy tiếp.

### 🔹 Cách hoạt động:
- ✅ **Tạo tín hiệu ngắt**: Do sự kiện như nhấn nút, tràn bộ đếm, nhận dữ liệu UART.
- ✅ **Xử lý ngắt**: CPU lưu trạng thái, thực thi **ISR (Interrupt Service Routine)**.
- ✅ **Tiếp tục chương trình chính** sau khi ISR kết thúc.

### 🔹 Ưu điểm của Interrupts:
- ✔ **Hiệu suất cao** – CPU không bị lãng phí vào vòng lặp kiểm tra sự kiện.
- ✔ **Phản hồi nhanh** – Ngay lập tức khi có sự kiện.
- ✔ **Tiết kiệm năng lượng** – CPU có thể vào chế độ ngủ và chỉ thức dậy khi có ngắt.

### 🔹 Ứng dụng:
- 🔸 Xử lý nút nhấn, debounce.
- 🔸 Nhận dữ liệu UART không bị mất.
- 🔸 Ngắt Timer để thực thi nhiệm vụ theo chu kỳ.
- 🔸 Xử lý tín hiệu từ cảm biến.

---

## 🔥 **2. So Sánh Polling vs Interrupt-Driven I/O**

### 🔹 Polling (Thăm dò)
Polling là phương pháp CPU liên tục kiểm tra trạng thái của một sự kiện (ví dụ: kiểm tra xem nút bấm có được nhấn hay không). Phương pháp này đơn giản nhưng tốn nhiều tài nguyên và có thể gây trễ khi phản hồi với sự kiện quan trọng.

### 🔹 Interrupt-Driven I/O
Interrupt-Driven I/O hoạt động theo cơ chế chỉ kích hoạt khi có sự kiện xảy ra, giúp CPU rảnh rỗi để thực hiện các tác vụ khác trong lúc chờ đợi.

### 🔹 So sánh
- **Hiệu suất**: Polling làm CPU tiêu tốn nhiều tài nguyên, trong khi Interrupt tối ưu hóa thời gian xử lý.
- **Độ trễ**: Polling có thể bị trễ, trong khi Interrupt phản ứng ngay lập tức.
- **Tiêu thụ năng lượng**: Polling tiêu hao nhiều năng lượng hơn, còn Interrupt giúp tiết kiệm năng lượng.
- **Mức độ phức tạp**: Polling dễ triển khai, nhưng Interrupt tối ưu hơn trong các ứng dụng yêu cầu phản hồi nhanh.

### 🔹 Ví dụ
Polling liên tục kiểm tra trạng thái của nút nhấn, trong khi Interrupt phát hiện ngay lập tức khi nút được nhấn.

➡ **Kết luận**: Nếu hệ thống yêu cầu xử lý nhanh và tiết kiệm tài nguyên, **Interrupt-Driven I/O** là lựa chọn tối ưu! ⚡

---

## 🕒 **3. Timers – Cấu Hình & Ứng Dụng**

### 🔹 Timers là gì?
➡️ Là bộ đếm phần cứng giúp đo thời gian, tạo tín hiệu PWM, và phát ngắt theo chu kỳ.

### 🔹 Ứng dụng:
- ✅ **Đo thời gian** (ví dụ: bấm giờ).
- ✅ **Tạo ngắt theo chu kỳ** (nhấp nháy LED).
- ✅ **PWM** – Điều khiển tốc độ động cơ, độ sáng LED.

### 🔹 Cách cấu hình Timer:
1. **Chọn Timer** (ví dụ: TIM1, TIM2).
2. **Cấu hình Prescaler** để điều chỉnh độ phân giải.
   - 📌 Công thức: 
     ```
     Prescaler = Tần số Clock / Tần số mong muốn
     ```
3. **Chọn chế độ đếm**: Lên, xuống hoặc lên/xuống.
4. **Cấu hình chu kỳ đếm (Period)**:
   - 📌 Công thức: 
     ```
     Period = Clock Timer / (Prescaler × Thời gian mong muốn)
     ```
5. **Bật ngắt Timer** nếu cần thực hiện tác vụ theo chu kỳ.
6. **Bắt đầu Timer** để đếm.

### 🔹 Kết hợp Timer và Interrupts:
- Cấu hình Timer để tạo ngắt khi tràn.
- Viết ISR để xử lý khi Timer ngắt.

---

## 💡 **4. Ứng Dụng Thực Tế Của Timer & Interrupts**

- ✅ **Real-Time Clock (RTC)** – Giữ thời gian chính xác.
- ✅ **PWM Generation** – Điều chỉnh tốc độ động cơ, độ sáng LED.
- ✅ **Lập lịch sự kiện** – Chạy các tác vụ định kỳ như đọc dữ liệu cảm biến.
- ✅ **Đo tín hiệu** – Đo tần số hoặc độ rộng xung của tín hiệu đầu vào.

---

👉 **Bạn đã từng làm việc với Timer và Interrupts chưa? Bạn thích dùng phương pháp nào hơn? Hãy chia sẻ trong comment nhé!** ⬇⬇

#EmbeddedSystems #Timers #Interrupts #IoT #Microcontroller
