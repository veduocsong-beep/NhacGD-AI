# Hướng dẫn thay đổi website Trái Tym Sách Tai

Phiên bản mẫu dùng React + Vite. Bạn không cần sửa bố cục để thay nội dung: phần lớn dữ liệu nằm ở `src/data.ts`, còn màu sắc nằm ở đầu file `src/styles.css`.

## 1. Thay tên thương hiệu và khẩu hiệu

Mở `src/data.ts`, tìm đoạn:

```ts
export const brand = {
  name: 'Trái Tym Sách Tai',
  tagline: 'Sáng tạo để thư giản, thư giản trong sáng tạo.',
  email: 'hello@traitymsachtai.example',
}
```

Đổi giá trị trong dấu nháy. Tên thương hiệu đang được dùng ở footer và cấu trúc thương hiệu; khẩu hiệu đang được hiển thị ở footer và phần câu chuyện trên trang chủ. Nếu muốn đổi tiêu đề lớn, tìm các chuỗi trong component tương ứng ở `src/main.tsx`.

## 2. Thay màu sắc

Mở `src/styles.css`, tìm khối `:root` ở đầu file. Các biến quan trọng là:

```css
--cobalt: #2457d6;      /* xanh thương hiệu */
--cobalt-dark: #183f9f; /* xanh hover */
--orange: #f2995d;      /* điểm nhấn cam */
--pink: #ef9bb2;        /* điểm nhấn hồng */
--paper: #fbfaf7;       /* nền sáng */
--ink: #182033;         /* chữ chính */
```

Chỉ cần thay mã hex, toàn bộ nút, liên kết, nhãn và điểm nhấn sẽ đổi theo. Các cover mẫu dùng thêm các lớp như `.cover-cobalt`, `.cover-orange`, `.cover-pink`, `.cover-mint` và các lớp game như `.game-sky`, `.game-sun`, `.game-leaf`, `.game-rose`.

## 3. Thêm hoặc sửa bài hát

Trong `src/data.ts`, mỗi bài hát là một object trong `songs`:

```ts
{
  slug: 'ten-bai-hat',
  title: 'Tên bài hát',
  artist: 'Tên nghệ sĩ',
  genre: 'Thể loại / Mood',
  duration: '03:20',
  year: '2026',
  description: 'Mô tả ngắn.',
  story: 'Câu chuyện hoặc cảm hứng sáng tác.',
  coverClass: 'cover-cobalt',
  audioUrl: '/audio/ten-bai-hat.mp3',
  featured: true,
}
```

- `slug` là phần URL; chỉ nên dùng chữ thường, số và dấu gạch ngang.
- `audioUrl` có thể là đường dẫn file MP3 trong `public/audio/` hoặc URL công khai.
- Để bài xuất hiện ở nhóm nổi bật trên trang chủ, thêm `featured: true` (dữ liệu mẫu hiện dùng vị trí đầu danh sách).
- Muốn dùng ảnh bìa thật, đặt ảnh vào `public/images/` rồi thêm `imageUrl: '/images/ten-anh.jpg'`. Khi có `imageUrl`, cover gradient mẫu sẽ tự chuyển sang ảnh.

## 4. Thêm hoặc sửa trò chơi Canva

Trong cùng file, sửa một object trong `games`:

```ts
{
  slug: 'ten-tro-choi',
  title: 'Tên trò chơi',
  subject: 'Môn học',
  grade: 'Lớp 6',
  duration: '10–15 phút',
  description: 'Mô tả ngắn.',
  objective: 'Mục tiêu học tập.',
  steps: ['Bước 1', 'Bước 2', 'Bước 3'],
  coverClass: 'game-sky',
  canvaUrl: 'https://www.canva.com/design/…',
}
```

`canvaUrl` là liên kết sẽ mở bằng tab mới khi học sinh bấm **Mở trò chơi Canva**. Ảnh minh họa có thể thêm bằng `imageUrl: '/images/ten-game.jpg'` theo cách giống bài hát.

## 5. Thêm file MP3 và ảnh vào dự án

Tạo các thư mục nếu chưa có:

```text
public/
├── audio/
│   └── bai-hat-cua-ban.mp3
└── images/
    └── anh-bia-cua-ban.jpg
```

Sau đó dùng đường dẫn bắt đầu bằng `/audio/` hoặc `/images/` trong `src/data.ts`. Tên file không nên có khoảng trắng hoặc ký tự đặc biệt.

## 6. Chạy và xem website

Trong thư mục dự án, chạy:

```bash
npm install
npm run dev
```

Website mẫu dùng cổng `3000`. Sau khi sửa dữ liệu, Vite sẽ tự cập nhật preview. Trước khi bàn giao bản mới, chạy:

```bash
npm run build
```

Nếu bạn thêm một route mới, hãy cập nhật cả `public/manus-routes.json` để hệ thống nhận diện đúng các trang.

> Lưu ý: form Liên hệ hiện chỉ là giao diện mẫu. Nó không gửi hay lưu dữ liệu lên máy chủ.
