# Dự đoán tỷ lệ chuyển đổi của khách hàng 
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
- **Specific Questions:**
  - [1] Nhóm khách hàng nào có xác suất chuyển đổi cao nhất?
  - [2] Các yếu tố nào ảnh hưởng lớn nhất đến việc chuyển đổi?
  - [3] Cần điều chỉnh ưu đãi như thế nào để tăng chuyển đổi?

# ANALYST
## [Question 1] Nhóm khách hàng nào có xác suất chuyển đổi cao nhất?





 
