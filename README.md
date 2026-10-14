# HCM-KS26-CNTT1_Session08_Ex03
# Bài 3: Onboarding lập trình viên mới

*Hướng dẫn cài đặt VS Code và thực hành trình bày tài liệu bằng Markdown*

## 1. Mục tiêu bài thực hành

Sau bài này, người học có thể cài đặt môi trường Python cơ bản trên VS Code, phân biệt phần giải thích với lệnh chạy trong Terminal, và sử dụng đúng **Inline Code**, **Code Block**, **Table** và **Task List** khi viết tài liệu Markdown.

## 2. Phân tích Input / Output (I/O)

| Thành phần | Mô tả |
|---|---|
| **Input** | Nội dung văn bản thô trong file `.md`, gồm tiêu đề bắt đầu bằng `#`, danh sách, dấu `|` tạo bảng, các đoạn lệnh và khối code đặt giữa ba dấu backtick. |
| **Xử lý** | Soạn nội dung bằng VS Code hoặc StackEdit; mở chế độ Preview để trình biên dịch Markdown đọc cú pháp và hiển thị nội dung. |
| **Output** | Tài liệu được render trên StackEdit với tiêu đề phân cấp, bảng so sánh rõ ràng, đoạn Python có syntax highlighting, chữ inline code dễ nhận biết và ô checklist có thể đánh dấu. |

Một lưu ý nhỏ: **Markdown là văn bản nguồn**, còn giao diện Preview là kết quả sau khi render. Tài liệu Word kèm theo là bản báo cáo trình bày để đọc và nộp, không thay thế file nguồn `.md`.

## 3. Hướng dẫn cài đặt VS Code

### Bước 1. Cài VS Code và Python

1. Truy cập [trang tải VS Code](https://code.visualstudio.com/download), chọn phiên bản cho Windows, macOS hoặc Linux rồi cài như hướng dẫn.
2. Truy cập [python.org](https://www.python.org/downloads/) và cài Python 3. Lưu ý: cài extension Python trong VS Code **không đồng nghĩa** máy đã có trình thông dịch Python.
3. Mở Terminal và kiểm tra Python đã hoạt động chưa.

**Terminal – Windows** (thử một trong hai lệnh):

```powershell
python --version
py --version
```

**Terminal – macOS / Linux**:

```bash
python3 --version
```

Nếu Terminal in ra số phiên bản Python 3, bước kiểm tra đã thành công.

### Bước 2. Cài extension và mở thư mục dự án

Trong VS Code, mở **Extensions** (`Ctrl+Shift+X` trên Windows/Linux hoặc `Cmd+Shift+X` trên macOS), tìm **Python** của Microsoft và bấm **Install**.

Sau đó mở Terminal tích hợp bằng menu **Terminal → New Terminal** và chạy:

```bash
mkdir onboarding-python
cd onboarding-python
code .
```

Nếu lệnh `code .` chưa nhận diện được, dùng **File → Open Folder** để mở thư mục `onboarding-python`. Trên macOS, có thể cần chạy lệnh **Shell Command: Install 'code' command in PATH** từ Command Palette.

### Bước 3. Chọn môi trường Python

Nhấn `Ctrl+Shift+P` hoặc `Cmd+Shift+P`, tìm **Python: Create Environment**, chọn **Venv** rồi chọn bản Python đã cài. Sau đó dùng **Python: Select Interpreter** để chọn môi trường `.venv` cho dự án.

### Bước 4. Chạy thử chương trình

Tạo file `kiem_tra.py`, nhập đoạn code ở mục 4 rồi lưu. Mở Terminal tại thư mục dự án và chạy lệnh phù hợp với máy.

**Terminal – Windows**:

```powershell
python kiem_tra.py
```

**Terminal – macOS / Linux** (nếu chưa kích hoạt `.venv`):

```bash
python3 kiem_tra.py
```

Trong môi trường `.venv` đã kích hoạt, thường có thể dùng `python kiem_tra.py` trên cả hai hệ điều hành.

## 4. Ví dụ Python có Syntax Highlighting

Trong đoạn dưới đây, `tasks` là danh sách công việc và trạng thái hoàn thành, `done` là số bước đã xong, `total` là tổng số bước, còn `project_dir` là đường dẫn thư mục hiện tại. Những tên ngắn này được đặt trong **Inline Code** để không bị lẫn vào phần văn bản giải thích.

```python
from pathlib import Path
import sys


def show_progress(tasks: dict[str, bool]) -> None:
    total = len(tasks)
    done = sum(tasks.values())
    print(f"Tiến độ: {done}/{total} bước")

    for name, completed in tasks.items():
        mark = "x" if completed else " "
        print(f"[{mark}] {name}")


def main() -> None:
    project_dir = Path.cwd()
    print("KIỂM TRA MÔI TRƯỜNG PYTHON")
    print(f"Phiên bản Python: {sys.version.split()[0]}")
    print(f"Thư mục dự án: {project_dir}")

    tasks = {
        "Cài VS Code": True,
        "Cài Python 3": True,
        "Chọn Python Interpreter": False,
        "Chạy thử chương trình": False,
    }
    show_progress(tasks)


if __name__ == "__main__":
    main()
```

Các giá trị `True` và `False` chỉ là **dữ liệu minh họa** để thử chương trình, không tự kiểm tra xem máy đã cài đặt xong thật hay chưa. Người học có thể thay đổi chúng để quan sát kết quả.

Khi chạy, chương trình sẽ in phiên bản Python, thư mục dự án và tiến độ (ví dụ `2/4 bước`). Khi xem trên StackEdit, phần code sẽ được đặt trong khối riêng và tô màu cú pháp Python.

## 5. So sánh StackEdit và VS Code

| Tiêu chí | StackEdit | VS Code |
|---|---|---|
| Mục đích chính | Soạn và xem trước tài liệu Markdown. | Viết, chạy và quản lý mã nguồn. |
| Ưu điểm nổi bật | Preview Markdown thuận tiện; dễ trình bày tiêu đề, bảng và checklist. | Có Terminal tích hợp, extension, gợi ý code và debug. |
| Điểm mạnh trong bài này | Kiểm tra kết quả render của file `.md`. | Cài Python, viết `kiem_tra.py` và thực thi chương trình. |
| Điều cần lưu ý | Không thay thế trình thông dịch Python. | Cần cài Python riêng và chọn đúng interpreter. |

**Nhận xét:** Hai công cụ không cạnh tranh trực tiếp trong bài này. VS Code phù hợp cho bước lập trình, còn StackEdit giúp kiểm tra tài liệu Markdown có dễ đọc và đúng định dạng hay không.

## 6. Escape ký tự đặc biệt trong Markdown

Khi muốn hiển thị dấu `*` hoặc `#` đúng như ký tự thông thường, đặt dấu gạch chéo ngược `\` ngay trước ký tự đó.

- **Văn bản nguồn:** `\*không in nghiêng\*` → **Hiển thị:** \*không in nghiêng\*
- **Văn bản nguồn:** `\# Tiêu đề ví dụ` → **Hiển thị:** \# Tiêu đề ví dụ

Nếu không escape, các dấu này có thể được hiểu là cú pháp in nghiêng hoặc tiêu đề, tùy vị trí sử dụng.

## 7. Task List kiểm tra tiến độ

Chỉ đánh dấu `[x]` khi đã tự kiểm tra bước tương ứng trên máy:

- [ ] Đã tải và cài VS Code.
- [ ] Đã cài Python 3 và xem được phiên bản trong Terminal.
- [ ] Đã cài extension Python của Microsoft.
- [ ] Đã tạo và mở thư mục `onboarding-python`.
- [ ] Đã tạo và chọn môi trường `.venv`.
- [ ] Đã tạo file `kiem_tra.py` và chạy không có lỗi.
- [ ] Đã mở file `.md` trên StackEdit và kiểm tra bảng, code block, checklist.
- [ ] Đã thử ký tự escape `\*` và `\#` để xem kết quả hiển thị.

## 8. Kết luận

Qua bài thực hành, em hiểu rõ hơn sự khác nhau giữa nội dung Markdown dạng text và giao diện sau khi render. Cách đặt lệnh Terminal trong code block riêng giúp tránh nhầm lẫn khi làm theo hướng dẫn; đồng thời, bảng so sánh và checklist giúp tài liệu dễ theo dõi hơn. Khi làm bài nhóm, em sẽ giữ cùng cách trình bày để người mới có thể cài đặt và kiểm tra từng bước.
