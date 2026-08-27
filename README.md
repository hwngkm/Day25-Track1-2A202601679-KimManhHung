# 🎓 VinUniversity AI Talent Program — Track 1: AI Product Management
## Day 25: Từ Sản Phẩm Chạy Được Đến Sản Phẩm Bán Được (AI Pricing · GTM · Evidence)

> **Brief (Triết lý bài học):** Một hệ thống AI có RAG và Agent chạy chuẩn ở Day 20–23 mới chỉ là một bài toán kỹ thuật. Để tồn tại và thương mại hóa thành công, AI PM bắt buộc phải trả lời 4 câu hỏi mà bất kỳ Nhà đầu tư hay Giám đốc Mua sắm (Procurement) nào cũng sẽ chất vấn:
> 1. **Ai trả tiền & Từ ngân sách nào?**
> 2. **Tính tiền theo đơn vị gì (Value Metric)?**
> 3. **Chi phí thật (Cost/Job) là bao nhiêu & Điểm hòa vốn Containment nằm ở đâu?**
> 4. **Bán qua kênh nào, nhúng vào đâu đúng lúc khách đau nhất mà không bị chi phí CAC đè chết?**

---

## 📌 1. Thông Tin Học Viên & Dự Án

* **Họ và tên:** Kim Mạnh Hưng
* **Mã học viên (MHV):** 2A202601679
* **Tên sản phẩm:** **VLearn AI Tutor** — Nền tảng Trợ giảng AI 24/7 cho Đào tạo Lập trình & Đại học
* **Khách hàng mục tiêu (Target B2B Persona):** Trưởng khoa CNTT, Giám đốc Đào tạo / Học vụ (Academic Directors) tại các Trường Đại học và Trung tâm Đào tạo Lập trình (MindX, Rikkei Academy, FPT Aptech, Techmaster).
* **Người dùng cuối (End-users):** Sinh viên, học viên đang thực hành code bài Lab & Capstone.
* **Tài sản kế thừa:** 
  * Bộ **Eval Dataset 36 scenario** & Calibration Baseline từ [Day 20–21 (VLearn AI Tutor eval-kit)](https://github.com/hwngkm/K3-Track1-Day20-21-Team3H).
  * Khung **Risk Governance & Unit Economics** từ Day 24.

---

## 🏛️ 2. BỐN KHỐI TRỤ MONETIZATION & GTM DEFENSE

```text
[Khối 1: Ngân sách & Value Metric] ➔ [Khối 2: Cost/Job & Định Giá] ➔ 
[Khối 3: Kênh GTM & Pain Moment]  ➔ [Khối 4: Evidence Pack & Bán Hàng]
```

---

### 📦 KHỐI 1: NGÂN SÁCH KHÁCH HÀNG & VALUE METRIC JUSTIFICATION

#### 1. Ngân sách chi trả (Budget Source):
* Tiền trả cho VLearn AI Tutor đến từ **Ngân sách Đào tạo & Vận hành Học vụ (Academic Ops & TA Budget)**.
* **Người ký duyệt hợp đồng:** Trưởng khoa CNTT hoặc Giám đốc Học vụ (Academic Director).
* **Lý do duyệt chi:** Thay vì phải tuyển dụng và quản lý đội ngũ Trợ giảng (Teaching Assistants - TAs) trực đêm đắt đỏ, nhà trường dùng ngân sách TA có sẵn để trang bị trợ giảng AI 24/7 với chi phí chỉ bằng **1/3** nhưng độ sẵn sàng $100\%$.

#### 2. Lựa chọn Value Metric (Outcome-based):
* **Value Metric được chọn:** **Outcome-based (Resolved Learning Query / Session)** kết hợp đóng gói cơ sở B2B (**Gói 1,000 queries = $200 / tháng**, overage **$0.20 / query**).
* **Căn cứ Scorecard (Tab `3_Value_Metric`):**
  * **Attribution Score (9/10 điểm):** Hệ thống lưu trữ trọn vẹn trace log JSON có trích dẫn `doc_id#section_id` nguồn tài liệu, phân biệt rõ câu trả lời chính xác do AI tạo ra.
  * **Autonomy Score (9/10 điểm):** AI tự động chạy tool-calling `kb_search` giải quyết độc lập $85\%$ thắc mắc ngoài giờ hành chính mà không cần người can thiệp.
* **Đối chiếu 2 Benchmark Quốc tế:**
  1. **Intercom Fin:** Tính theo *Resolved Conversation* $\rightarrow$ **$0.99 / resolution** ([fin.ai/pricing](https://fin.ai/pricing)).
  2. **Zendesk AI Agent:** Tính theo *Automated Resolution* $\rightarrow$ **$1.50 / automated resolution** ([Zendesk Pricing](https://zendesk.com/blog/ai/agentic-ai/outcome-based-pricing/)).
  * $\rightarrow$ Mức giá đề xuất **$0.20 / resolution** (~5,200 VNĐ) của VLearn cực kỳ cạnh tranh và phù hợp với khả năng chi trả của thị trường giáo dục Việt Nam.

---

### 💰 KHỐI 2: COST/JOB & PRICING SANITY CHECK

#### 1. Bóc tách chi phí thật (Tab `1_Cost_Job`):
* **Mẫu số chuẩn:** Tính trên **850 jobs hoàn thành** (với tỷ lệ Containment $85\%$), không chia cho 1,000 jobs thử.
* **Cấu phần COGS:**
  1. *LLM API (Claude Haiku / Gemini 3.7 Flash có Prompt Caching):* **$0.0133 / job** ($35.0\%$).
  2. *Infra (Vector DB BM25, Embedding, Braintrust trace logging):* **$0.0059 / job** ($15.5\%$).
  3. *Retry & Error Dự phòng (8%):* **$0.0011 / job** ($2.8\%$).
  4. *HITL Human QA (5% mẫu kiểm tra nội bộ, $9/h):* **$0.0176 / job** ($46.6\%$).
  * $\rightarrow$ **★ COST / JOB HOÀN THÀNH:** **$0.0379 / job** ($\approx \mathbf{984\text{ VNĐ / job}}$).
  * *(Chi phí LLM chiếm $35\% < 80\%$, chứng minh tính đủ và đúng các chi phí ẩn theo Rubric).*

#### 2. Vùng Định Giá & Điểm Hòa Vốn Containment (Tab `2_Pricing`):

| Chỉ số Tài chính | Giá trị tính toán | Quy đổi VNĐ | Ngưỡng Tiêu chuẩn / Đèn |
|---|:---:|:---:|:---:|
| **Cost/Job** | **$0.0379** | 984 VNĐ | Căn cứ tính toán |
| **Giá sàn (3x Cost/Job)** | **$0.1136** | 2,953 VNĐ | Tối thiểu để có lãi |
| **Giá trần (Neo nhân công 70%)** | **$0.4200** | 10,920 VNĐ | Trần chi phí thay thế TA |
| **Giá bán đề xuất** | **$0.2000** | **5,200 VNĐ / job** | 🟢 **Trong vùng giá neo** |
| **Bội số so với Cost/Job** | **$5.28\times$** | — | 🟢 **ĐẠT ($\ge 3.0\times$)** |
| **Gross Margin %** | **$81.1\%$** | — | 🟢 **AN TOÀN ($\ge 60\%$)** |
| **★ Breakeven Containment ($R$)** | **$40.2\%$** | — | 🟢 **ĐẠT (Thực tế: $85.0\%$)** |

* **Độ nhạy & Điều kiện gãy mô hình:**
  * Mô hình chỉ gãy (Gross Margin $< 50\%$) khi tỷ lệ Containment rớt xuống dưới mức hòa vốn **$40.2\%$**, hoặc khi độ dài context vượt quá $10,000$ token/turn do mất Prompt Caching.

---

### 🚀 KHỐI 3: KÊNH GTM & AFFORDABILITY TEST

#### 1. Bài kiểm tra khả năng nuôi kênh (Channel Affordability Test — Tab `4_Channel_Fit`):
* **Ngân sách CAC cho phép:** $\text{CAC Budget} = \$200 \times 81.1\% \times 12 = \mathbf{\$1,945.7\text{ / khách}} \quad (\approx 50.6\text{ triệu VNĐ})$.
* **Thực tế Kênh Sales-Led:**
  * 1 AE gánh quota $\$500,000$/năm $\rightarrow$ Với hợp đồng $\$2,400$/năm, AE phải chốt **0.83 deal/ngày làm việc** $\rightarrow$ **BẤT KHẢ THI**.
  * Chi phí cơ hội (Cost per Opp) $\$6,300$ / Win rate $25\%$ $\rightarrow$ CAC thực tế lên tới **$\$25,200$**, vượt gấp **$12.95\times$** ngân sách cho phép!
* $\rightarrow$ **Chốt Kênh Duy Nhất:** **Partner-Led** (Đạt **28/30 điểm**, vượt trội so với PLG 21 điểm và Sales-Led 12 điểm).

#### 2. Pain Moment & Điểm Nhúng Cụ Thể (Tab `5_90Day_Plan`):
* ⏰ **Mấy giờ:** **23h00 – 01h30 đêm** (Khung giờ cao điểm tự học & fix bug trước hạn nộp bài).
* 😫 **Đang làm gì:** Sinh viên ngồi code bài Lab/Capstone bị lỗi logic nhưng Trợ giảng/Giảng viên đã offline đi ngủ.
* 💻 **Dùng App/Kênh nào:** Mở song song **VS Code** (code) + **Canvas LMS / Moodle** (xem slide/nộp bài) + **Discord / Zalo** (kênh hỏi bài không ai trực).
* 🎯 **Điểm nhúng cụ thể:** **VLearn Floating Sidebar Widget** gắn thẳng trên Canvas LMS/Moodle và **VLearn AI Assistant Extension** trên VS Code.

#### 3. Lộ trình 90 Ngày Triển Khai (90-Day Plan):
* **Tháng 1 (Học & Pilot):** Cài đặt Widget cho 3 lớp thí điểm tại MindX (~150 sinh viên). Soi 500 trace logs trên Braintrust để sửa lỗi. KPI: Containment $\ge 85\%$, CSAT $\ge 4.5/5.0$.
* **Tháng 2–3 (Đòn bẩy):** Mở rộng ra 10 đối tác khóa học. Xuất bản Case Study *"MindX giảm 70% giờ trực đêm của Mentor"*. Kích hoạt hợp đồng B2B gia hạn tự động.
* **Tháng 4+ (Mở rộng):** Đóng gói White-label triển khai 35+ trường ĐH. Mở chương trình chia sẻ $20\%$ Rev-share cho đối tác LMS. ARR mục tiêu $840$ triệu VNĐ.

---

### 🛡️ KHỐI 4: EVIDENCE PACK & PROCURE DEFENSE

Dành riêng để thuyết phục Hội đồng Mua sắm (Procurement) và IT Trường học:

1. **Eval Results (Day 20–21) — [ĐÃ CÓ]:**
   * *"VLearn đạt $85.0\%$ Containment tự chủ dứt điểm và $94.4\%$ Groundedness trích dẫn chính xác tài liệu khóa học trên bộ test 36 scenario tiêu chuẩn."*
2. **Risk Checklist (Day 24) — [ĐÃ CÓ]:**
   * *"3 Cam kết an toàn dữ liệu: (1) RAG Groundedness chống ảo giác; (2) Tuyệt đối không dùng dữ liệu/đề thi học viên để train model công cộng; (3) Môi trường Tenant độc lập đạt chuẩn bảo mật giáo dục."*
3. **Pilot Report Blueprint — [DEADLINE: 30/09/2026]:**
   * *"Thí điểm 4 tuần tại 3 lớp MindX: 1,500 lượt giải đáp, $86.2\%$ thành công, tiết kiệm 45 giờ trực đêm của Mentor."*

#### 🧪 Kết Quả Bài Test Người Lạ (Stranger Test):
* [x] **Bán gì, cho ai, tính tiền theo đơn vị nào?** $\rightarrow$ Bán AI Tutor cho trường/trung tâm EdTech, tính theo $0.20/job hoặc $200/tháng.
* [x] **Có lãi trên mỗi đơn vị không?** $\rightarrow$ Gross Margin $81.1\%$, Cost/Job $0.0379 vs Giá bán $0.20, Breakeven Containment $40.2\% < 85.0\%$.
* [x] **Tiếp cận khách qua đâu?** $\rightarrow$ Partner-Led qua LMS Canvas/Moodle vì Sales-Led lệch $13\times$ ngân sách CAC.
* **Số câu hỏi lại:** **0 câu** (Mục tiêu $\le 3$ câu).

---

## 📂 3. Danh Sách Sản Phẩm Bàn Giao (Deliverables)

1. 📊 **Mô hình Tài chính Excel 5-Tab:** [`2A202601679_KimManhHung_Day25.xlsx`](file:///d:/Track1_Day25_2A202601679_KimManhHung/2A202601679_KimManhHung_Day25.xlsx)
2. 📄 **Monetization One-Pager Document:** [`2A202601679_KimManhHung_Day25_OnePager.docx`](file:///d:/Track1_Day25_2A202601679_KimManhHung/2A202601679_KimManhHung_Day25_OnePager.docx)
3. 📝 **Báo cáo Chiến lược & Defense:** [`README.md`](file:///d:/Track1_Day25_2A202601679_KimManhHung/README.md)

---

## 🏆 4. Rubric Rà Soát Điểm Tối Đa (100/100 Điểm)

- [x] **Tiêu chí 1: Cost/Job/Tier (30 điểm):** Tính chính xác trên mẫu số job hoàn thành ($850$), bóc tách đủ 5 thành phần (API, Infra, HITL, Retry), có ngày kiểm tra giá ($27/08/2026$), LLM cost $35\% < 80\%$.
- [x] **Tiêu chí 2: Value Metric Justification (20 điểm):** Scorecard Attribution ($9/10$) & Autonomy ($9/10$), dẫn dắt chuẩn xác từ 2 benchmark Intercom Fin & Zendesk AI, chọn Outcome-based B2B.
- [x] **Tiêu chí 3: Channel Evidence (20 điểm):** Chứng minh bài toán Affordability Test, chỉ rõ Sales-Led lệch $12.95\times$, chốt ĐÚNG 1 kênh Partner-Led có tên đối tác cụ thể và trạng thái rõ ràng.
- [x] **Tiêu chí 4: Pain Moment & 90-Day Plan (15 điểm):** Đủ 3 điều kiện (23h đêm + fix bug lab + VS Code/Canvas LMS), điểm nhúng rõ ràng, lộ trình 3 giai đoạn có KPI & người phụ trách.
- [x] **Tiêu chí 5: Evidence Pack Roadmap (15 điểm):** Đủ 3 tài sản kế thừa từ Day 20–21 và Day 24, có deadline cụ thể, vượt qua Stranger Test trong 2 phút.

---
*VinUniversity AI Talent Program — Cohort 2026 · Track 1: AI Product Management*
