# Trái Tym Sách Tai — Kế hoạch triển khai

## Phạm vi đã xác nhận
Website nhiều trang bằng tiếng Việt cho thương hiệu “Trái Tym Sách Tai”, giới thiệu bài hát do người dùng tạo bằng AI (Sona, Flow Music) và trò chơi giáo dục tạo bằng Canva. Phiên bản đầu chạy hoàn toàn phía trình duyệt, dùng dữ liệu mẫu dễ thay thế, có nghe nhạc MP3 trực tuyến, tải MP3, liên kết trò chơi Canva, không đăng nhập, cơ sở dữ liệu, thanh toán hay máy chủ. Không kết nối GitHub, không đẩy mã nguồn và không xuất bản.

## Thiết kế
- **Design Movement:** Editorial neo-brutalist mềm mại kết hợp minimal art direction và visual language giáo dục tươi sáng.
- **Core Principles:** rõ ràng trước, vui nhưng không trẻ con, giàu khoảng trắng, thao tác trực tiếp.
- **Color Philosophy:** trắng ngà tạo cảm giác nhẹ và nghệ thuật; cobalt blue là màu nhận diện có năng lượng và độ tin cậy; cam/hồng dùng như điểm nhấn ấm áp để dẫn hướng; mực than giữ khả năng đọc.
- **Layout Paradigm:** bố cục tạp chí theo các dải nội dung lệch nhịp, hero chia đôi cân bằng, thẻ nội dung xếp theo nhịp dọc thay vì dashboard lưới đều.
- **Signature Elements:** logo trái tim–tai–sách, đường viền cobalt dày, nhãn pill màu cam/hồng và các đường sóng âm.
- **Interaction Philosophy:** nút và thẻ phản hồi rõ ràng, hover nâng nhẹ, audio player luôn dễ nhận biết; liên kết ngoài được đánh dấu.
- **Animation:** reveal trượt nhẹ theo chiều dọc, pulse tối thiểu ở nút phát, không dùng animation gây phân tán khi học hoặc nghe.
- **Typography System:** Be Vietnam Pro cho nội dung và UI; Fraunces cho tiêu đề lớn để tạo sắc thái nghệ thuật. Hierarchy: display 56–72px desktop, heading 32–44px, body 16–18px, label 12–13px uppercase.
- **Brand Essence:** một không gian nơi âm nhạc AI và hoạt động học tập gặp nhau để giúp người trẻ thư giãn, khám phá và học chủ động. Tính cách: sáng tạo, ấm áp, tinh nghịch.
- **Brand Voice:** thân thiện, giàu hình ảnh, ngắn gọn và khích lệ. Ví dụ: “Bấm phát, để ý tưởng cất tiếng.” / “Chơi một vòng, nhớ thêm một điều.”
- **Wordmark & Logo:** dấu trái tim cobalt chứa hình tai cách điệu, bên trong tai là một quyển sách mở; wordmark đặt cạnh mark với nhịp chữ editorial.
- **Signature Brand Color:** cobalt blue `#2457D6`.

## Cấu trúc kỹ thuật
- `src/` chứa ứng dụng React, route và component dùng chung.
- `src/data/` chứa dữ liệu mẫu bài hát, trò chơi, thông tin thương hiệu để thay thế sau.
- `src/components/` chứa Header, Footer, LogoMark, AudioPlayer, SongCard, GameCard.
- `src/pages/` chứa Home, Music, SongDetail, Games, GameDetail, About, Contact.
- `src/styles/` chứa token màu, typography và layout responsive.
- `public/manus-routes.json` khai báo các route trang.
- `public/audio/` giữ chỗ cho MP3 thật; bản demo dùng đường dẫn mẫu có thể thay.

## Luồng trang
`/` → `/am-nhac` và `/tro-choi`; các thẻ dẫn đến `/am-nhac/:slug` hoặc `/tro-choi/:slug`; Header có `/gioi-thieu`, `/lien-he`. Trang chi tiết bài hát có audio controls và download; trang chi tiết trò chơi có nút mở Canva.

## Dữ liệu mẫu
Dùng 4 bài hát mẫu và 4 trò chơi mẫu với ảnh minh họa gradient/CSS hoặc ảnh remote ổn định, tất cả đều có nhãn “Dữ liệu mẫu”. Liên kết Canva và MP3 mẫu được thiết kế để thay thế trong một file dữ liệu duy nhất.
