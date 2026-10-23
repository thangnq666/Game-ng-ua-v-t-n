# Đường Đua Vô Tận

Game đua xe arcade góc nhìn sau xe, chạy hoàn toàn trong trình duyệt. Toàn bộ game nằm trong một file `index.html` duy nhất — không build, không phụ thuộc, không gọi mạng. Mở file bằng trình duyệt là chơi được.

## Chơi thử

Mở trực tiếp `index.html`, hoặc chạy một server tĩnh:

```bash
python3 -m http.server 8000
# rồi mở http://localhost:8000
```

## Điều khiển

| Thao tác | Bàn phím | Cảm ứng |
| --- | --- | --- |
| Bẻ lái | `←` `→` hoặc `A` `D` | Chạm giữ nửa trái / nửa phải màn hình |
| Phanh | `↓` hoặc `S` | — |
| Turbo | `Space` | Nút TURBO |
| Bắt đầu / chơi lại | `Enter` hoặc `Space` | Nút trên màn hình |

Ba nút tròn ở đáy màn hình hiện ra trên thiết bị cảm ứng và màn hình hẹp.

## Luật chơi

- Xe tự tăng tốc. Tốc độ trần tăng dần theo quãng đường đã chạy.
- **Vượt sát** xe khác (lướt qua mà không chạm) cộng hệ số điểm và nạp thanh turbo. Thanh đầy thì bật turbo để nhân đôi điểm và tăng tốc độ trần.
- **Chạm đuôi xe phía trước** là kết thúc, trừ khi xe đang có khiên hoặc còn giáp húc.
- **Ra lề đường** làm mòn lốp: mỗi lần ra một mức phạt cố định, cộng thêm hao mòn theo thời gian nằm ngoài mặt nhựa. Thanh lốp đầy là nổ lốp, dừng cuộc đua. Chạy trên đường thì lốp hồi dần.
- **Chạy chậm quá** sẽ bị xe phía sau tông vào đuôi. Chip đỏ cảnh báo khi có xe nhanh hơn đang áp sát cùng làn.
- **Người và thú băng qua đường** bất chợt: người chạy bộ, người đi xe đạp, công nhân cầu đường, người ôm ván lướt sóng, hươu, chó hoang, lợn rừng; ở vùng địa chấn là đá lở nằm giữa làn. Đâm phải thì mất gần nửa tốc độ, hỏng lốp nặng và mất combo; né kịp thì cộng điểm.

## Vật phẩm trên đường

| Vật phẩm | Tác dụng |
| --- | --- |
| Vàng | Cộng thẳng quãng đường (nhân theo chỉ số từng xe) và hồi một ít độ bền lốp |
| Khiên | Miễn va chạm trong 5–12 giây tùy xe, phá luôn xe đâm vào |
| Bom | Thổi bay toàn bộ xe trong 80 m phía trước |

## Địa hình và thời tiết

Đường tự sinh ngẫu nhiên mỗi ván, ghép từ 9 chương. Mỗi chương có một vùng thời tiết, một khung cảnh ven đường và một số làn riêng, chuyển tiếp mượt giữa các chương.

**Bảy vùng thời tiết:** Trời Quang, Cơn Mưa Xối Xả, Cao Nguyên Băng, Vùng Địa Chấn, Miệng Núi Lửa, Vùng Lốc Xoáy, Sương Mù Dày. Mỗi vùng có bảng màu, độ dày sương, chiều cao camera và độ bám đường riêng.

**Năm khung cảnh ven đường:** khu đô thị (cao ốc có ô cửa sáng đèn), nông thôn (hàng cây, nhà kho), đường biển (một bên là mặt nước, bên kia hàng dừa), khu chiến sự (xác xe cháy, bao cát, cột khói), trường đua (khán đài, chồng lốp, cổng vạch sọc).

**Địa hình đặc biệt:** cầu vượt có lan can và không có lề, vòng xoáy là khúc cua gắt kéo dài, cùng đồi dốc và chuỗi cua chữ S.

**Số làn** thay đổi giữa 2, 3 và 5 làn; mặt đường rộng hẹp theo đó.

**Ngày và đêm** chạy thành chu kỳ liên tục, nhanh hơn khi xe chạy nhanh. Ban đêm đèn đường, đèn pha và cửa sổ nhà sáng lên; ban ngày thì tắt dần.

**Mưa và tuyết làm đường trơn.** Hướng đánh lái và hướng xe thực sự trượt là hai đại lượng tách biệt: trên đường khô chúng gần như trùng nhau, khi ướt hoặc đóng băng thì bánh bám chậm lại và xe còn trôi tiếp sau khi nhả phím. Vũng nước và mảng băng hiện trên mặt đường, cán phải là bị đá ngang và mất thêm độ bám trong khoảng một giây rưỡi.

**Địa chấn, lốc xoáy và sương mù hạn chế người chơi:** rung chấn làm tay lái chỉ còn 58% hiệu lực, gió giật còn 70%, sương mù dày cắt tầm nhìn xuống còn vài chục mét.

## Ga-ra

Mười xe, mỗi xe một hướng đánh đổi rõ rệt về tốc độ, độ nhạy lái, giáp húc, độ bền lốp, hệ số thu vàng, tốc độ nạp turbo, thời gian giữ khiên và độ bám trong từng kiểu thời tiết.

| Xe | Thế mạnh |
| --- | --- |
| Thiên Lang GT | Cân bằng toàn diện |
| Hỏa Kỳ Lân R | Tốc độ tối đa, nhưng trượt khi mưa tuyết và không có giáp |
| Bạch Tuyết Vương | Bám đường trên băng tuyết, lốp dày |
| Vũ Phong Lữ Khách | Mưa bão và lốc xoáy |
| Địa Chấn Mãnh Thú | Trụ vững khi rung chấn, húc đổ 2 xe trong 20 m |
| Hỏa Diệm Sơn Quân | Chịu nhiệt vùng núi lửa |
| Kim Cương Thiết Giáp | Húc đổ 3 xe, lốp bền nhất, nhưng chậm và ì |
| Ngân Hà Phi Tiễn | Nạp turbo gần gấp đôi, thân nhẹ và không có giáp |
| Hoàng Kim Đại Sứ | Thu vàng hơn gấp đôi |
| Tử Thần U Linh | Lái nhạy nhất, giữ khiên lâu nhất |

Xe đã chọn, kỷ lục điểm và thiết lập âm thanh được lưu trong `localStorage` của trình duyệt.

## Kỹ thuật

- Dựng hình giả 3D theo kiểu phân đoạn đường: mỗi đoạn đường mang độ cong, độ cao, số làn và bề rộng riêng, chiếu lên màn hình rồi vẽ từ xa về gần.
- Vật lý chạy ở bước cố định 1/60 giây với bộ tích lũy, tách khỏi tốc độ khung hình.
- Camera động: nghiêng và dịch tầm nhìn vào trong khúc cua, mở góc nhìn khi tăng tốc, nâng hạ theo từng vùng, rung theo địa chấn và gió giật.
- Xe, người, cảnh vật và hiệu ứng thời tiết đều vẽ bằng Canvas 2D, không dùng ảnh.
- Âm thanh động cơ tổng hợp bằng Web Audio, tần số bám theo tốc độ.

## Giấy phép

Chưa đặt. Thêm file `LICENSE` nếu cần công bố.
