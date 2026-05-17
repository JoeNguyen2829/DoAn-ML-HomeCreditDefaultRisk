[README.md](https://github.com/user-attachments/files/27903962/README.md)
# 🏦 Home Credit Default Risk — ML Course Project

> Dự đoán khả năng vỡ nợ tín dụng tiêu dùng sử dụng Machine Learning  
> Đồ án môn học Machine Learning | Nhóm 2 thành viên

---

## 📋 Giới thiệu

Đây là đồ án môn học Machine Learning thực hiện bài toán **Binary Classification** trên bộ dữ liệu thực tế từ [Home Credit Default Risk (Kaggle)](https://www.kaggle.com/c/home-credit-default-risk).

**Mục tiêu:** Dự đoán xác suất một người vay sẽ gặp khó khăn trong việc hoàn trả khoản vay, hỗ trợ tổ chức tài chính đưa ra quyết định cho vay chính xác và công bằng hơn.

---

## 📊 Dataset

| Thuộc tính | Giá trị |
|---|---|
| Nguồn | [Kaggle — Home Credit Default Risk](https://www.kaggle.com/c/home-credit-default-risk) |
| Số mẫu | 246,009 hồ sơ vay vốn |
| Số đặc trưng | 122 → 230 (sau feature engineering) |
| Biến mục tiêu | TARGET (0: trả đúng hạn / 1: khó khăn trả nợ) |
| Mất cân bằng lớp | 91.9% / 8.1% |

---

## 🔬 Pipeline

```
📁 Data Loading
    ↓
📊 EDA (6 biểu đồ phân tích)
    ↓
🛠️ Preprocessing
    ├── Xử lý missing values (xóa >60%, điền median/mode)
    ├── Label Encoding (4 cột nhị phân)
    ├── One-Hot Encoding (12 cột đa giá trị)
    ├── Feature Engineering (+5 features mới)
    └── Stratified Split 80/20 + StandardScaler + Class Weighting
    ↓
🤖 Huấn luyện 4 mô hình
    ├── Logistic Regression (baseline)
    ├── Decision Tree
    ├── Random Forest
    └── LightGBM
    ↓
📈 Đánh giá & So sánh
    ├── Confusion Matrix
    ├── ROC Curve
    ├── Feature Importance
    └── Overfitting Analysis
```

---

## 🏆 Kết quả

| Mô hình | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---|---|---|---|---|
| Logistic Regression | 0.6885 | 0.1621 | 0.6853 | 0.2622 | 0.7519 |
| Decision Tree | 0.6380 | 0.1417 | **0.6886** | 0.2351 | 0.7153 |
| Random Forest | 0.6957 | 0.1612 | 0.6581 | 0.2590 | 0.7387 |
| **LightGBM** ⭐ | **0.7332** | **0.1819** | 0.6584 | **0.2850** | **0.7658** |

> **Mô hình tốt nhất: LightGBM** với ROC-AUC = **0.7658**
>
> *Top Kaggle competition đạt ROC-AUC ~0.806 với feature engineering nâng cao từ 7 file dữ liệu. Nhóm đạt 0.7658 chỉ với file chính và 5 features tự tạo.*

---

## 💡 Insights nổi bật

- **EXT_SOURCE_1/2/3** — điểm tín dụng bên ngoài là features quan trọng nhất, tương quan mạnh nhất với TARGET
- **CREDIT_TERM** (feature tự tạo) đứng **#1** trong LightGBM Feature Importance — vượt qua các features gốc
- **Logistic Regression** chỉ kém LightGBM 0.0139 ROC-AUC nhưng hoàn toàn không overfit → phù hợp cho production
- **Class Weighting 11.4×** giúp tất cả mô hình đạt Recall >65% cho class vỡ nợ

---

## 🛠️ Công nghệ sử dụng

![Python](https://img.shields.io/badge/Python-3.12-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-green)
![LightGBM](https://img.shields.io/badge/LightGBM-4.x-red)
![Pandas](https://img.shields.io/badge/Pandas-2.x-blue)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-purple)

| Thư viện | Mục đích |
|---|---|
| `pandas`, `numpy` | Xử lý dữ liệu |
| `scikit-learn` | ML models, preprocessing, metrics |
| `lightgbm` | Gradient boosting |
| `matplotlib`, `seaborn` | Visualization |
| `Google Colab` | Môi trường thực thi |

---

## 📁 Cấu trúc project

```
DoAn-ML-HomeCreditDefaultRisk/
│
├── DoAn_ML_HomeCreditDefaultRisk.ipynb   # Notebook chính
│
└── README.md                              # File này
```

> Dataset không được upload do kích thước lớn (~228MB).  
> Tải tại: [kaggle.com/c/home-credit-default-risk](https://www.kaggle.com/c/home-credit-default-risk)

---

## 🚀 Hướng dẫn chạy

1. Clone repo:
```bash
git clone https://github.com/JoeNguyen2829/DoAn-ML-HomeCreditDefaultRisk.git
```

2. Tải dataset từ Kaggle và upload `application_train.csv` lên Google Drive

3. Mở notebook trên Google Colab — click badge **Open in Colab** ở đầu notebook

4. Cập nhật đường dẫn file trong **Cell 3**

5. Chạy: **Runtime → Run all** (bỏ qua Cell 2 nếu đã giải nén)

---

## 📚 Tài liệu tham khảo

- Ke, G. et al. (2017). LightGBM: A Highly Efficient Gradient Boosting Decision Tree. *NIPS 2017*
- Breiman, L. (2001). Random Forests. *Machine Learning*, 45, 5–32
- Pedregosa, F. et al. (2011). Scikit-learn: Machine Learning in Python. *JMLR*, 12, 2825–2830

---

## 👥 Nhóm thực hiện

| Thành viên | Vai trò |
|---|---|
| Thành viên 1 | EDA, Feature Engineering, Modeling |
| Thành viên 2 | Preprocessing, Evaluation, Report |

*Đồ án Môn Học Machine Learning — 2026*
