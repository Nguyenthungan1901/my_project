# my_project

## Giới thiệu
Dự án này phân tích dữ liệu bóng đá từ nhiều nguồn để cung cấp cái nhìn tổng quan chi tiết về các giải đấu, trận đấu, câu lạc bộ và cầu thủ.

## Các bảng dữ liệu chính
Dữ liệu được chia thành 8 bảng chính:
1. **Appearance**: Lần Xuất Hiện của Cầu Thủ
2. **Games**: Trận Đấu
3. **Clubs**: Câu Lạc Bộ
4. **Players**: Cầu Thủ
5. **Competitions**: Giải Đấu
6. **Club_games**: Trận Đấu Giữa Các Câu Lạc Bộ
7. **Game_events**: Sự Kiện Trong Trận Đấu
8. **Player_valuation**: Định Giá Cầu Thủ

## Tổng quan về các bảng thống kê chính
### Appearance_minutes
- **Giới thiệu**: Bảng thống kê số lần xuất hiện và thời gian thi đấu của cầu thủ.
- **Cột chính**:
  - `player_id`: Mã cầu thủ
  - `player_name`: Tên cầu thủ
  - `total_appearances`: Tổng số lần xuất hiện
  - `total_minutes_played`: Tổng số phút thi đấu
- **Input**:
  - Dữ liệu từ bảng `Players`: Thông tin về mã và tên cầu thủ.
  - Dữ liệu từ bảng `Appearance`: Thông tin về số lần xuất hiện và thời gian thi đấu của cầu thủ.
- **Output**:
  - Thống kê tổng số lần xuất hiện và tổng số phút thi đấu của từng cầu thủ.
  - Kết quả được sắp xếp theo số lần xuất hiện và thời gian thi đấu giảm dần.

### Foreign_Player
- **Giới thiệu**: Bảng thống kê cầu thủ nước ngoài trong các câu lạc bộ.
- **Cột chính**:
  - `club_id`: Mã câu lạc bộ
  - `club_name`: Tên câu lạc bộ
  - `foreigners_number`: Số lượng cầu thủ nước ngoài
  - `foreigners_percentage`: Tỷ lệ phần trăm cầu thủ nước ngoài
  - `calculated_foreigners_percentage`: Tỷ lệ cầu thủ nước ngoài tính toán
  - `foreigners_level`: Mức độ cầu thủ nước ngoài (Cao, Vừa, Thấp)
  - `competition_name`: Tên giải đấu
  - `competition_type`: Loại giải đấu
- **Input**:
  - Thông tin về các câu lạc bộ từ bảng `Clubs`
  - Dữ liệu giải đấu từ bảng `Competitions` để xác định giải đấu và loại giải đấu liên quan.
- **Output**:
  - Thống kê về số lượng và tỷ lệ phần trăm cầu thủ nước ngoài trong các câu lạc bộ, phân loại mức độ cầu thủ nước ngoài trong từng giải đấu.

### Yellow_Red_Cards
- **Giới thiệu**: Bảng thống kê số thẻ vàng và thẻ đỏ trong các giải đấu.
- **Cột chính**:
  - `competition_id`: Mã giải đấu
  - `competition_name`: Tên giải đấu
  - `total_yellow_cards`: Tổng số thẻ vàng
  - `total_red_cards`: Tổng số thẻ đỏ
  - `total_players`: Tổng số cầu thủ
- **Input**:
  - Dữ liệu về các giải đấu từ bảng `Competitions`
  - Thông tin về số thẻ vàng và thẻ đỏ từ bảng `Appearance`
- **Output**:
  - Thống kê tổng số thẻ vàng và thẻ đỏ trong từng giải đấu cùng với tổng số cầu thủ tham gia từng giải đấu.

### Club_Player_Market
- **Giới thiệu**: Bảng thống kê danh sách cầu thủ và giá trị thị trường của họ trong các câu lạc bộ.
- **Cột chính**:
  - `club_id`: Mã câu lạc bộ
  - `club_name`: Tên câu lạc bộ
  - `total_players`: Tổng số cầu thủ
  - `total_market_value`: Tổng giá trị thị trường
  - `avg_market_value`: Giá trị thị trường trung bình
  - `players_with_goals`: Số lượng cầu thủ ghi bàn
- **Input**:
  - Dữ liệu về các câu lạc bộ từ bảng `Clubs`
  - Thông tin về giá trị thị trường và danh sách cầu thủ từ bảng `Players`
  - Thông tin về bàn thắng từ bảng `Appearance`
- **Output**:
  - Thống kê tổng số cầu thủ và tổng giá trị thị trường của họ trong từng câu lạc bộ cùng với giá trị thị trường trung bình và số lượng cầu thủ ghi bàn trong mỗi câu lạc bộ.

---

