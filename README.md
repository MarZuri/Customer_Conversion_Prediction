- **Data Source:** [Marketing Promotion Campaign Uplift Modelling](https://www.kaggle.com/datasets/davinwijaya/customer-retention?fbclid=IwY2xjawHeNDhleHRuA2FlbQIxMAABHWyLPXhPlUlKiUWAZVWv5eNClppVT-AFlQ9-Qsyltcbvqc0z95cOClxxqw_aem_tUVt0yIy8o5Cn1O2GF6OCg)
- **Structure:**
  - ```recency```: Số tháng kể từ lần mua hàng cuối cùng của khách hàng. *Ví dụ: recency = 2: khách hàng đã mua lần cuối cách đây 2 tháng.*
  - ```history```: Tổng giá trị giao dịch của khách hàng trong quá khứ (lịch sử chi tiêu). *Ví dụ: Nếu history = 500, nghĩa là khách hàng đã chi tổng cộng 500 USD trong quá khứ.* 
  - ```used_discount```: Khách hàng có từng sử dụng giảm giá trong các giao dịch trước đây không? (1: Có, 0: Không). *Ví dụ: Nếu used_discount = 1, khách hàng đã sử dụng giảm giá trước đây.*
  - ```used_bogo```: Khách hàng có từng sử dụng hình thức "Mua một tặng một" (Buy One Get One) trong lịch sử giao dịch không (1: Có, 0: Không).
  - ```zip_code```: Khu vực khách hàng sinh sống (Surburban, Rural, Urban).
  - ```is_referral```: Khách hàng có đến từ kênh giới thiệu hay không (1: Có, 0: Không).
  - ```channel```: Kênh khách hàng sử dụng để chuyển đổi (Phone, Web, Multichannel). *Ví dụ: Nếu channel = Phone, khách hàng thường sử dụng kênh điện thoại để mua hàng.*
  - ```offer```: Loại ưu đãi được gửi đến khách hàng (Buy One Get One, Discount, No Offer). *Ví dụ: offer = Discount: Gửi ưu đãi giảm giá cho khách hàng.* 
  - ```conversion```(Biến mục tiêu): Khách hàng có chuyển đổi hay không (1: Chuyển đổi, 0: Không chuyển đổi).

- **Model:** —-----------------nội dung fill sau—-----------------
- **Algorithms:** —-----------------nội dung fill sau—-----------------
- **Tools:** Python, Tableau


# INTRODUCTION
- **Yêu cầu:** Dự đoán tỷ lệ chuyển đổi (conversion rate) của khách hàng cho chiến dịch marketing sắp tới
- **Audience:** Giám đốc Marketing (CMO)
- **Business Goals:**
  - Tăng tỷ lệ chuyển đổi khách hàng: Công ty muốn tối ưu hóa ROI (Return on Investment).
  - Tăng doanh thu: Ưu tiên tiếp cận và chuyển đổi những khách hàng có giá trị giao dịch lịch sử cao.
- **Specific Questions:** Nhóm khách hàng nào có xác suất chuyển đổi cao nhất?
  


# [QUESTION] NHÓM KHÁCH HÀNG NÀO CÓ XÁC SUẤT CHUYỂN ĐỔI CAO NHẤT?
## 1. Ảnh hưởng của việc sử dụng ưu đãi trước đây
Tỷ lệ chuyển đổi chung của khách hàng là 14.68%, trong khi tỷ lệ không chuyển đổi là 85.32%.\

![1](https://github.com/user-attachments/assets/ab844b35-469f-4a0d-ac82-4535f6446bfb)

Đáng chú ý, toàn bộ khách hàng chuyển đổi đều đã từng sử dụng các ưu đãi trước đây. Trong đó, 44.1% khách hàng chỉ sử dụng Buy One Get One, 38.8% chỉ sử dụng Discount, và 17.1% sử dụng cả hai loại ưu đãi.\
*=> Điều này cho thấy nhóm khách hàng chuyển đổi chủ yếu đến từ những người chỉ sử dụng một loại ưu đãi, đặc biệt là Buy One Get One.*\
*=> Buy One Get One nên được đầu tư và phát triển trong các chiến dịch tiếp thị tiếp theo để thu hút và giữ chân khách hàng.*\

![2](https://github.com/user-attachments/assets/1f7675b8-586f-478e-a29d-7be13b656f74)

### Tóm lại với khách hàng sử dụng ưu đãi trước đây:
- Tỷ lệ chuyển đổi trung bình: 100% khách hàng chuyển đổi đã sử dụng ưu đãi trước đây.
- Khách hàng sử dụng "Buy One Get One" có xác suất chuyển đổi cao hơn 1.45% so với khách hàng chỉ sử dụng Discount => Không có sự chênh lệch quá nhiều.
  
---

## 2. Ảnh hưởng của khu vực địa lý
**Định hướng:**
- Kiểm tra tỉ lệ chuyển đổi trung bình của từng khu vực để biết khu vực nào có tỷ lệ chuyển đổi cao nhất?
- Đối với mỗi khu vực:
  - Kiểm tra xem loại offer nào hiệu quả nhất? 
  - Với mỗi loại offer thì thực hiện trên channel nào sẽ mang lại hiệu quả cao nhất?
  - Kiểm tra xem liệu khách hàng đã từng sử dụng ưu đãi trước đây có chuyển đổi tốt hơn hay không?
  - Các yếu tố khác như history hay (recency) có làm thay đổi hiệu quả của từng loại offer không?

Tỷ lệ chuyển đổi trung bình theo khu vực cho thấy Rural có hiệu quả cao nhất với 18.81%, vượt trội so với Suburban (13.99%) và Urban (13.90%).

![3](https://github.com/user-attachments/assets/2569637e-904a-481b-b5a6-a92381c19050)


### Phân tích khu vực Rural
Loại ưu đãi có tỷ lệ chuyển đổi cao nhất trong Rural là Discount. Discount (22.695%) > Buy One Get One (18.264%) > No Offer (15.355%).

![4](https://github.com/user-attachments/assets/3e9e2cbb-a88c-41d1-b632-171e64122ae6)


**Hiệu quả của từng kênh với ưu đãi Discount:**
- Multichannel: 26.02%
- Web: 24.15%
- Phone: 20.27%\

*=> Đối với ưu đãi Discount thì Multichannel đạt được tỷ lệ chuyển đổi cao nhất*


**Hiệu quả của từng kênh với ưu đãi Buy One Get One:**
- Web: 20.78%
- Multichannel: 18.88%
- Phone: 15.55%\

*=> Đối với ưu đãi Buy One Get One thì Web mang lại hiệu quả cao hơn*

![5](https://github.com/user-attachments/assets/255563b8-9078-431f-81e0-47eab7a9d0eb)


**So sánh khách hàng sử dụng ưu đãi trước đây:**
- Discount:
  - Đã sử dụng: 19.42%
  - Chưa sử dụng: 18.07%

- Buy One Get One:
  - Đã sử dụng: 20.51%
  - Chưa sử dụng: 16.76%
    
*=> Tỷ lệ chuyển đổi của nhóm đã từng dùng ưu đãi trước đây đều cao hơn nhóm chưa từng dùng*

<img width="945" alt="Screenshot 2025-01-15 at 20 40 30" src="https://github.com/user-attachments/assets/e67e4d17-8f8a-4dc0-a9e8-94a9e40fd6ed" />


**Theo lịch sử giao dịch (history) và số tháng kể từ lần mua hàng cuối cùng (recency) cho thấy:**
- Discount:
  - History: 1001-1500(USD)
  - Recency: 7-12 tháng\
=> Đạt tỷ lệ cao nhất (33.33%)

- Buy One Get One (BOGO):
  - History: 501-1000(USD)
  - Recency: 4-6 tháng
    
=> Đạt tỷ lệ chuyển đổi cao nhất (26.6%)

<img width="1004" alt="Screenshot 2025-01-15 at 20 51 00" src="https://github.com/user-attachments/assets/69eeaf05-b6cf-4bc8-92e1-34c25f687c69" />


**Tóm lại trong Rural:**
- Discount và Multichannel là sự kết hợp hiệu quả nhất trong việc tăng tỷ lệ chuyển đổi.
- Web là kênh tốt nhất cho Buy One Get One.
- Nhóm khách hàng đã từng sử dụng ưu đãi trước đây, đặc biệt là Buy One Get One, có xu hướng chuyển đổi cao hơn.
- Xác định nhóm khách hàng dựa trên lịch sử giao dịch và số tháng kể từ lần mua hàng cuối cùng:
  - Với Discount: Tập trung vào nhóm có tổng giá trị giao dịch trong quá khứ từ 1001-1500 USD và đã mua hàng lần cuối cách đây từ 7-12 tháng.
  - Với Buy One Get One: Tập trung vào nhóm có tổng giá trị giao dịch trong quá khứ từ 501-1000 USD và đã mua lần cuối cách đây từ 4-6 tháng.

### Phân tích khu vực Suburban
Trong Suburban, loại ưu đãi có tỷ lệ chuyển đổi cao nhất là Discount. Discount (17.335%) > Buy One Get One (14.787%) > No Offer (9.901%).

![11](https://github.com/user-attachments/assets/d4e78df3-be05-4da5-a84b-f9f87bbc3825)

**Hiệu quả của từng kênh với ưu đãi Discount:**
- Multichannel: 20.42%
- Web: 18.42%
- Phone: 15.36%

**Hiệu quả của từng kênh với ưu đãi Buy One Get One:**
- Multichannel: 18.56%
- Web: 15.35%
- Phone: 13.20%

*=> Multichannel là kênh tốt nhất cho cả hai ưu đãi Discount và Buy One Get One*

![12](https://github.com/user-attachments/assets/0a035f4c-4e70-478f-9c0d-063176fea498)


**So sánh khách hàng sử dụng ưu đãi trước đây:**
- Discount:
  - Đã sử dụng: 14.19%
  - Chưa sử dụng: 13.76%

- Buy One Get One:
  - Đã sử dụng: 15.75%
  - Chưa sử dụng: 11.85%\

*=> Ở cả hai ưu đãi thì nhóm khách hàng đã sử dụng ưu đãi đều > nhóm khách hàng chưa sử dụng ưu đãi trước đây*

<img width="917" alt="Screenshot 2025-01-16 at 00 35 27" src="https://github.com/user-attachments/assets/116d4587-1296-4155-8d7e-d9a76fd0c71a" />



**Lịch sử giao dịch (history) và số tháng kể từ lần mua hàng cuối cùng (recency) cho thấy:**
- Discount:
  - History: 1001-1500 (USD)
  - Recency: 4-6 tháng\
    
*=> Đạt tỷ lệ cao nhất (100%)*

- Buy One Get One:
  - History: 1001-1500(USD)
  - Recency: 4-6 tháng\
  
*=> Đạt tỷ lệ chuyển đổi cao nhất (28.26%)*

<img width="1047" alt="Screenshot 2025-01-16 at 00 39 37" src="https://github.com/user-attachments/assets/4037fd64-43ae-4b8f-8c24-f86c841a80a6" />


**Tóm lại trong Suburban:**
- Discount và Multichannel là sự kết hợp hiệu quả nhất để tăng tỷ lệ chuyển đổi.
- Web là kênh thứ hai tốt nhất cho cả 2 ưu đãi Discount và Buy One Get One.
- Nhóm khách hàng đã từng sử dụng ưu đãi Buy One Get One trước đây có xu hướng chuyển đổi cao hơn nhóm đã dùng Discount.
- Nhóm khách hàng có tỷ lệ chuyển đổi cao ở cả 2 ưu đãi là nhóm có tổng giá trị giao dịch từ 1001-1500 USD và đã mua hàng lần cuối cách đây từ 4-6 tháng.

### Phân tích khu vực Urban
Urban có tỷ lệ chuyển đổi thấp nhất trong ba khu vực. Loại ưu đãi có tỷ lệ chuyển đổi cao nhất là Discount. Discount (17.646%) > Buy One Get One (14.375%) > No Offer (9.681%).

![17](https://github.com/user-attachments/assets/8ba069a9-c556-470c-b0c8-1520fc4f18ef)


**Hiệu quả của từng kênh với ưu đãi Discount:**
- Multichannel: 20.26% 
- Web: 18.74%.
- Phone: 15.79%
  
=> Multichannel là kênh hiệu quả khi kết hợp với ưu đãi Discount

**Hiệu quả của từng kênh với ưu đãi Buy One Get One:**
- Web: 16.07% 
- Multichannel: 16.00%
- Phone: 12.29%

*=> Web là kênh hiệu quả khi kết hợp với ưu đãi Buy One Get One*

![19](https://github.com/user-attachments/assets/61769a75-9d6b-4147-9db5-623e31822bff)

**So sánh khách hàng sử dụng ưu đãi trước đây:**
- Discount:
  - Đã sử dụng: 13.99%
  - Chưa sử dụng: 13.80%
- Buy One Get One:
  - Đã sử dụng: 15.46%.
  - Chưa sử dụng: 12.00%\

*=> Tỷ lệ chuyển đổi của nhóm đã từng dùng ưu đãi trước đây đều cao hơn nhóm chưa từng dùng*

<img width="1036" alt="Screenshot 2025-01-16 at 00 45 42" src="https://github.com/user-attachments/assets/4f63003c-185a-4b3f-b1e1-d266b86a6fb1" />


**Lịch sử giao dịch (history) và số tháng kể từ lần mua hàng cuối cùng (recency) cho thấy:**
- Discount:
  - History: >3000(USD) và 2501-3000 (USD)
  - Recency: 0-3 tháng và 7-12 tháng

=> Cả 2 nhóm đều đạt tỷ lệ cao nhất (100%)

- Buy One Get One:
  - History: 1501-2000(USD)
  - Recency: 7-12 tháng

=> Đạt tỷ lệ chuyển đổi cao nhất (100%)

<img width="1038" alt="Screenshot 2025-01-16 at 00 48 35" src="https://github.com/user-attachments/assets/9bf0dc87-1ec2-431a-80b6-9768e058dc78" />


**Tóm lại trong Urban:**
- Discount và Multichannel là sự kết hợp hiệu quả nhất tại Urban. 
- Web cũng là kênh hiệu quả, đặc biệt với ưu đãi Buy One Get One.
- Khách hàng đã từng sử dụng ưu đãi trước đây, đặc biệt Buy One Get One, có tỷ lệ chuyển đổi cao hơn.
- Đối với nhóm khách hàng sử dụng ưu đãi Discount có 2 nhóm đều đạt tỷ lẹ chuyển đổi cao:
  - Nhóm đã mua hàng lần cuối < 3 tháng có giá trị giao dịch lớn 3000 USD 
  - Nhóm đã mua hàng lần cuối cách đây từ 7-12 tháng, có giá trị giao dịch 2500-3000 USD
- Đối với nhóm khách hàng sử dụng ưu đãi Buy One Get One, có tổng giá trị giao dịch từ 1500-2000 USD và lần cuối mua cách đây từ 7-12 tháng

---

### Tóm lại ảnh hưởng của khu vực địa lý:
- Discount và Multichannel nên là trọng tâm của các chiến lược tiếp thị do hiệu quả nhất quán trên các khu vực.
- Web là kênh quan trọng khi triển khai ưu đãi Buy One Get One, nhắm vào nhóm khách hàng có lịch sử giao dịch trung bình (1501-2000) và thời gian mua hàng từ 4-12 tháng.
- Việc tái kích hoạt khách hàng từng sử dụng ưu đãi trước đây, đặc biệt với Buy One Get One, có tiềm năng tăng tỷ lệ chuyển đổi cao.
- Nếu chiến dịch nhắm vào nhóm khách hàng có giá trị giao dịch lớn thì nên tập trung vào khu vực Urban.

---

## 1.3. Ảnh hưởng của kênh (channel)
**Định hướng:** Xác định xem kênh nào hiệu quả nhất khi triển khai các ưu đãi tại các khu vực.

**Hiệu quả tổng thể của các kênh:**
- Multichannel: 17.17%
- Web: 15.94%
- Phone: 12.72%
*=> Hiệu quả tổng thể của các kênh cho thấy Multichannel dẫn đầu*


Khi xét ưu đãi trên từng kênh, Discount hiệu quả nhất trên cả Multichannel (21.15%) và Web (19.44%)
*=> Khẳng định vai trò quan trọng của hai kênh này trong việc thúc đẩy chuyển đổi*

![28](https://github.com/user-attachments/assets/00ced097-2654-498d-9cb7-272ce6039514)

Xét theo khu vực, Web (20.50%) và Multichannel (20.70%) đều hiệu quả nhất tại Rural, trong khi Multichannel tiếp tục dẫn đầu tại Suburban và Urban. Tuy nhiên, phân tích thống kê cho thấy không có sự khác biệt lớn giữa các kênh (p-value > 0.05), mặc dù Multichannel nổi bật hơn trong việc tăng tỷ lệ chuyển đổi tại các khu vực Rural và Suburban.\
*=> Nhấn mạnh tầm quan trọng của việc tối ưu hóa Multichannel, đặc biệt tại các khu vực trọng điểm*

![29](https://github.com/user-attachments/assets/cde1be19-bd36-4583-81b1-0c80df733244)


### Tóm lại ảnh hưởng của kênh:
**[1] Multichannel:**
- Tỷ lệ chuyển đổi trung bình: 17.17%.
- Là kênh hiệu quả nhất, dẫn đầu trong cả Discount và Buy One Get One, đặc biệt mạnh tại các khu vực Rural và Suburban.
- Không có sự khác biệt lớn về hiệu quả giữa các khu vực nhưng luôn dẫn đầu tỷ lệ chuyển đổi.
  
**[2] Web:**
- Tỷ lệ chuyển đổi trung bình: 15.94%.
- Hiệu quả thứ hai khi kết hợp với ưu đãi Discount, đặc biệt là khách hàng tại khu vực Rural 

**[3] Phone:**
- Tỷ lệ chuyển đổi trung bình: 12.72%.
- Kênh ít hiệu quả nhất, phù hợp hơn với khách hàng Rural không sử dụng ưu đãi.

**Đặc biệt:**
- Multichannel nên là ưu tiên hàng đầu để tối ưu hóa tỷ lệ chuyển đổi.
- Web là kênh quan trọng thứ hai, đặc biệt khi triển khai ưu đãi Discount.
- Phone có tiềm năng ở Rural, nhưng cần cải thiện hiệu quả tổng thể khi áp dụng ưu đãi.

## [ANSWER QUESTION 1] NHÓM KHÁCH HÀNG TIỀM NĂNG
**[1] Nhóm khách hàng tiềm năng nhất:**
- Khu vực: Urban.
- Kênh sử dụng: Multichannel 
- Ưu đãi: Discount, ưu tiên khách hàng đã sử dụng Discount trước đây.
- Giá trị giao dịch trong quá khứ và lần cuối mua hàng cách đây:
  - Giá trị giao dịch: >3000 USD
  - Lần cuối mua cách đây: <3 tháng
  - Ưu tiên nhóm thứ hai: 
    - Giá trị giao dịch: 2501-3000 USD
    - Lần cuối mua cách đây: 7-12 tháng


**[2] Nhóm khách hàng tiềm năng thứ hai:**
- Khu vực: Suburban.
- Kênh sử dụng: Multichannel 
- Ưu đãi: Discount, ưu tiên khách hàng đã sử dụng Buy One Get One trước đây
- Giá trị giao dịch trong quá khứ và lần cuối mua hàng cách đây:
  - Giá trị giao dịch: 1001-1500
  - Lần cuối mua cách đây: 4-6 tháng
 
**[3] Nhóm khách hàng tiềm năng thứ ba:**
- Khu vực: Rural.
- Kênh sử dụng: Multichannel
- Ưu đãi: Discount (tỷ lệ chuyển đổi: 22.695%), ưu tiên khách hàng đã sử dụng Buy One Get One trước đây
- Giá trị giao dịch trong quá khứ và lần cuối mua hàng cách đây:
  - Giá trị giao dịch: 1001-1500 USD
  - Lần cuối mua cách đây: 7-12 tháng



 
