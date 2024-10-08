## Tổng Hợp Và Giải Thích Các Lệnh Git Cơ Bản:

**1. Khởi tạo và cấu hình:**

* **`git init`**: Khởi tạo repository Git mới trong thư mục hiện tại.
* **`git config --global user.name "Tên của bạn"`**: Cấu hình tên người dùng Git.
* **`git config --global user.email "email@example.com"`**: Cấu hình email người dùng Git.

**2. Quản lý thay đổi:**

* **`git status`**: Xem trạng thái của repository, bao gồm các thay đổi chưa được theo dõi, theo dõi và đã staging.
* **`git add <tên_tệp>`**: Thêm thay đổi của tệp vào staging area để chuẩn bị commit.
* **`git add .`**: Thêm tất cả thay đổi của tất cả các tệp vào staging area.
* **`git commit -m "Thông điệp commit"`**: Ghi lại các thay đổi đã staging vào repository với một thông điệp mô tả.
* **`git diff`**: Xem sự khác biệt giữa working directory và staging area.
* **`git diff --staged`**: Xem sự khác biệt giữa staging area và commit gần nhất.

**3. Làm việc với branches:**

* **`git branch`**: Liệt kê tất cả các branch trong repository.
* **`git branch <tên_branch>`**: Tạo một branch mới.
* **`git checkout <tên_branch>`**: Chuyển sang một branch khác.
* **`git checkout -b <tên_branch>`**: Tạo và chuyển sang một branch mới.
* **`git merge <tên_branch>`**: Hợp nhất branch đã chỉ định vào branch hiện tại.
* **`git branch -d <tên_branch>`**: Xóa branch đã chỉ định.

**4. Làm việc với remote repository:**

* **`git remote add origin <địa_chỉ_remote>`**: Thêm remote repository với tên "origin" và địa chỉ đã chỉ định.
* **`git remote -v`**: Xem tất cả các remote repository đã được cấu hình.
* **`git clone <địa_chỉ_remote>`**: Sao chép repository từ remote repository về máy local.
* **`git push origin <tên_branch>`**: Đẩy các commit từ branch local lên remote repository.
* **`git pull origin <tên_branch>`**: Lấy và hợp nhất các commit từ remote repository vào branch local.

**5. Xem lịch sử commit:**

* **`git log`**: Xem lịch sử commit của branch hiện tại.
* **`git log --oneline`**: Xem lịch sử commit một cách ngắn gọn trên một dòng.
* **`git log --graph`**: Xem lịch sử commit với biểu đồ phân nhánh.

**6. Hoàn tác thay đổi:**

* **`git checkout -- <tên_tệp>`**: Hoàn tác thay đổi của tệp trong working directory về trạng thái giống commit gần nhất.
* **`git reset HEAD <tên_tệp>`**: Bỏ staging của tệp.
* **`git revert <commit_id>`**: Tạo một commit mới để hoàn tác thay đổi của commit đã chỉ định.

**7. Các lệnh hữu ích khác:**

* **`git help <lệnh>`**: Xem hướng dẫn chi tiết về một lệnh cụ thể.
* **`git stash`**: Lưu tạm thời các thay đổi chưa commit vào stash.
* **`git stash pop`**: Lấy ra các thay đổi từ stash.
* **`git rm <tên_tệp>`**: Xóa tệp khỏi working directory và staging area.
* **`git mv <tên_tệp_cũ> <tên_tệp_mới>`**: Đổi tên tệp.

Đây chỉ là một số lệnh Git cơ bản. Có rất nhiều lệnh và tùy chọn khác nhau cho phép bạn làm việc với Git một cách linh hoạt và hiệu quả. Bạn có thể tìm hiểu thêm về các lệnh Git nâng cao trên trang web chính thức của Git: [https://git-scm.com/](https://git-scm.com/)
