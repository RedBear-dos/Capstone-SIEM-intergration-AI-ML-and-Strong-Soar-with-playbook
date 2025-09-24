# Mini-SOC cho SMEs dựa trên Wazuh, AI & SOAR

## 1. Vấn đề nghiên cứu (Problem Statements)

### Bối cảnh  
Trong kỷ nguyên **chuyển đổi số**, các **doanh nghiệp vừa và nhỏ (SMEs)** ngày càng trở thành mục tiêu tấn công mạng tinh vi. **SOC (Security Operation Center)** là giải pháp quan trọng giúp giám sát, phát hiện và phản ứng kịp thời, nhưng SMEs gặp nhiều rào cản so với tập đoàn lớn:  
- **Thiếu nhận thức và nhân sự chuyên môn** (Rombaldo et al., 2023).  
- **Hệ thống lỗi thời, thiếu đầu tư công nghệ và đào tạo** (Tetteh, 2024).  
- **Mức độ triển khai an ninh thông tin không đồng đều, nhiều đơn vị chưa áp dụng biện pháp cơ bản** (Lill et al., 2025).  
- **Tại Việt Nam**: SMEs thiếu hụt nhân sự ATTT, ngân sách hạn chế → bị động khi có sự cố (Viettel IDC, 2025).  

➡️ SMEs chịu áp lực từ môi trường đe dọa phức tạp nhưng lại **thiếu tài chính và nhân lực** để xây dựng SOC truyền thống.

### Vấn đề cụ thể  
Các giải pháp **SIEM thương mại** hiện nay đều tập trung cho doanh nghiệp lớn → SMEs khó tiếp cận do:  
- **Chi phí cao** (tính theo log ingest hoặc asset).  
- **Yêu cầu đội ngũ chuyên môn** để vận hành, viết rule, xử lý cảnh báo.  
- **Mức độ phù hợp thấp**: nhiều tính năng nâng cao (UEBA, ML, SOAR) nhưng SMEs khó tận dụng, gây lãng phí.  

### So sánh chi phí – nhân sự – phù hợp với SMEs  

| **SIEM**             | **Chi phí** | **Yêu cầu nhân sự** | **Mức độ phù hợp SMEs** |
|----------------------|-------------|----------------------|--------------------------|
| **Microsoft Sentinel** | ~$5.22/GB (PAYG); ~$342.52/ngày cho 100GB | Cao – cần SOC team có kinh nghiệm | Quá đắt, phức tạp |
| **IBM QRadar**       | ~12,074.40 USD/năm (SIEM) + ~22,704 USD/năm (SOAR); mô hình tính EPS/FPM | Cao – cần chuyên gia correlation | Chủ yếu cho doanh nghiệp lớn |
| **Elastic Security** | Từ $131/tháng (Platinum) | Trung bình – cần kỹ năng DevOps & Elastic | Có thể cân nhắc nhưng vẫn cao cho SMEs |
| **Wazuh (OSS)**      | Miễn phí (OSS), chỉ tốn hạ tầng; Cloud: từ ~$571/tháng (≤100 agent) | Thấp – có dashboard, rule có sẵn | Rất phù hợp (chi phí thấp, dễ triển khai, mở rộng với AI & SOAR) |

### Kết luận vấn đề  
SMEs cần một **giải pháp SOC tối ưu hơn**:  
- **Giám sát & phòng thủ hiệu quả**.  
- **Giảm chi phí & nhân lực vận hành**.  
- **Phù hợp quy mô SMEs**.  

➡️ Đề xuất: xây dựng **mini-SOC dựa trên Wazuh OSS**, tích hợp **AI** (giảm cảnh báo giả) và **SOAR** (tự động phản ứng sự cố).  

---

## 2. Mục tiêu của đề tài (Project Objectives)

### Mục tiêu tổng quát  
Xây dựng **mô hình mini-SOC cho SMEs** dựa trên **Wazuh (SIEM OSS)**, kết hợp **AI (Random Forest)** và **SOAR (Shuffle)** để:  
- **Nâng cao khả năng phát hiện & phản ứng trước mối đe dọa**.  
- **Giảm can thiệp thủ công, tối ưu chi phí vận hành**.  

### Mục tiêu cụ thể  
1. **Triển khai hệ thống SIEM (Wazuh):**  
   - Thu thập log đa nguồn: Linux, Windows, Web Server, Database, Mail Server, Firewall.  
   - Phân tích & cảnh báo bảo mật.
   - Sơ đồ cấu trúc về SIEM và phân bổ Agent.

![Uploading SIEM Diagram-Trang-1.drawio (3).png…]()
![Uploading SIEM Diagram-Trang-1.drawio (3).png…]()


2. **Tích hợp AI (Random Forest):**  
   - Phân loại log & cảnh báo.  
   - Giảm cảnh báo giả (false positives).  

3. **Tích hợp SOAR (Shuffle):**  
   - Xây dựng playbook tự động hóa phản ứng: chặn IP, gửi cảnh báo, xử lý sự cố.  

4. **Đảm bảo tính phù hợp SMEs:**  
   - Chi phí thấp, dễ triển khai, yêu cầu ít nhân lực.  
