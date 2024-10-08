## Tổng Hợp Các Lệnh Git Chi Tiết

Bài viết này tổng hợp các lệnh Git được phân loại theo chức năng, bao gồm mô tả chi tiết và ví dụ minh họa.

**Lưu ý:** 
* `<tên_tệp>` đại diện cho tên tệp hoặc thư mục.
* `<tên_branch>` đại diện cho tên của branch.
* `<commit_id>` đại diện cho ID của commit (hash SHA-1).
* `<địa_chỉ_remote>` đại diện cho địa chỉ của remote repository.


### 1. Cấu hình Git

* **`git config --global user.name "<Tên của bạn>"`:**  Đặt tên người dùng Git toàn cục.
    * Ví dụ: `git config --global user.name "John Doe"`
* **`git config --global user.email "<email@example.com>"`:** Đặt email người dùng Git toàn cục.
    * Ví dụ: `git config --global user.email "john.doe@example.com"`
* **`git config --list`:** Liệt kê tất cả các cấu hình Git hiện tại.
* **`git config --global core.editor "<editor>"`:** Đặt trình soạn thảo văn bản mặc định cho Git (ví dụ: `vim`, `nano`).

### 2. Khởi tạo & Sao chép Repository

* **`git init`:**  Khởi tạo một repository Git mới trong thư mục hiện tại.
* **`git clone <địa_chỉ_remote>`:** Sao chép (clone) một repository từ xa về máy local.
    * Ví dụ: `git clone https://github.com/username/repository.git`

### 3. Quản lý Thay Đổi

* **`git status`:** Hiển thị trạng thái của working directory và staging area.
* **`git add <tên_tệp>`:** Thêm thay đổi của tệp vào staging area.
    * Ví dụ: `git add index.html`
* **`git add .`:**  Thêm tất cả thay đổi của tất cả các tệp vào staging area.
* **`git reset <tên_tệp>`:**  Bỏ staging của tệp.
    * Ví dụ: `git reset header.css`
* **`git diff`:** Hiển thị sự khác biệt giữa working directory và staging area.
* **`git diff --staged`:** Hiển thị sự khác biệt giữa staging area và commit gần nhất.
* **`git commit -m "<thông điệp commit>"`:** Tạo một commit mới với thông điệp mô tả.
    * Ví dụ: `git commit -m "Cập nhật giao diện trang chủ"`
* **`git commit -a -m "<thông điệp commit>"`:** Tự động staging tất cả các thay đổi của tệp đã được theo dõi và tạo commit.

### 4. Làm việc với Branch

* **`git branch`:** Liệt kê tất cả các branch trong repository.
* **`git branch <tên_branch>`:** Tạo một branch mới.
    * Ví dụ: `git branch feature/login`
* **`git checkout <tên_branch>`:** Chuyển sang một branch khác.
    * Ví dụ: `git checkout feature/login`
* **`git checkout -b <tên_branch>`:** Tạo và chuyển sang một branch mới.
    * Ví dụ: `git checkout -b hotfix/bug-123`
* **`git merge <tên_branch>`:** Hợp nhất branch đã chỉ định vào branch hiện tại.
    * Ví dụ: `git merge feature/login`
* **`git branch -d <tên_branch>`:** Xóa branch đã chỉ định.
    * Ví dụ: `git branch -d feature/login`
* **`git branch -D <tên_branch>`:**  Xóa branch (ngay cả khi chưa được merge).
    * Ví dụ: `git branch -D feature/login`

### 5. Làm việc với Remote Repository

* **`git remote`:** Liệt kê tất cả các remote repository đã được cấu hình.
* **`git remote -v`:**  Liệt kê tất cả các remote repository đã được cấu hình (bao gồm URL).
* **`git remote add <tên_remote> <địa_chỉ_remote>`:** Thêm một remote repository mới.
    * Ví dụ: `git remote add origin https://github.com/username/repository.git`
* **`git remote remove <tên_remote>`:**  Xóa một remote repository.
* **`git fetch <tên_remote>`:** Tải xuống tất cả các thay đổi từ remote repository nhưng không merge chúng.
* **`git pull <tên_remote> <tên_branch>`:**  Tải xuống và merge các thay đổi từ remote repository vào branch local.
    * Ví dụ: `git pull origin main`
* **`git push <tên_remote> <tên_branch>`:**  Đẩy (push) các commit từ local branch lên remote repository.
    * Ví dụ: `git push origin main`

### 6. Xem Lịch Sử & Thông Tin Commit

* **`git log`:** Hiển thị lịch sử commit của branch hiện tại.
* **`git log --oneline`:** Hiển thị lịch sử commit một cách ngắn gọn trên một dòng.
* **`git log --graph`:** Hiển thị lịch sử commit với biểu đồ phân nhánh.
* **`git log -p`:** Hiển thị chi tiết thay đổi của mỗi commit.
* **`git show <commit_id>`:** Hiển thị thông tin chi tiết của một commit cụ thể.
* **`git blame <tên_tệp>`:** Hiển thị ai đã thay đổi từng dòng code của tệp.

### 7. Hoàn tác Thay Đổi

* **`git checkout -- <tên_tệp>`:** Hoàn tác thay đổi của tệp trong working directory về trạng thái giống commit gần nhất.
* **`git revert <commit_id>`:**  Tạo một commit mới để hoàn tác thay đổi của commit đã chỉ định.
* **`git reset <commit_id>`:**  Di chuyển HEAD và branch hiện tại về commit đã chỉ định. Có 3 chế độ:
    * `--soft`: Giữ nguyên thay đổi trong staging area và working directory.
    * `--mixed` (mặc định): Giữ nguyên thay đổi trong working directory, đưa thay đổi từ staging area về working directory.
    * `--hard`: Xóa tất cả thay đổi trong staging area và working directory.
* **`git reset --hard HEAD`:** Hoàn tác tất cả thay đổi trong working directory và staging area về commit gần nhất.

### 8. Lưu trữ Thay đổi Tạm Thời

* **`git stash`:** Lưu trữ tạm thời các thay đổi chưa commit vào stash.
* **`git stash list`:** Liệt kê tất cả các stash.
* **`git stash pop`:**  Lấy ra thay đổi từ stash và xóa stash đó.
* **`git stash apply`:** Lấy ra thay đổi từ stash nhưng không xóa stash đó.
* **`git stash drop`:**  Xóa một stash cụ thể.

### 9. Làm việc với Tag

* **`git tag`:** Liệt kê tất cả các tag.
* **`git tag <tên_tag>`:**  Tạo một tag mới tại commit hiện tại.
* **`git tag -a <tên_tag> -m "<thông điệp tag>"`:** Tạo một tag mới với thông điệp mô tả.
* **`git tag <tên_tag> <commit_id>`:** Tạo một tag mới tại commit đã chỉ định.
* **`git push origin <tên_tag>`:**  Đẩy tag lên remote repository.
* **`git tag -d <tên_tag>`:** Xóa tag local.
* **`git push origin :refs/tags/<tên_tag>`:** Xóa tag trên remote repository.


### 10. Cấu hình nâng cao & lệnh khác

* **`.gitignore`:**  Tệp cấu hình để bỏ qua các tệp và thư mục không muốn theo dõi.
* **`git config --global alias.<tên_alias> "<lệnh_git>"`:** Tạo alias (lệnh tắt) cho các lệnh Git.
    * Ví dụ: `git config --global alias.co "checkout"`
* **`git rm <tên_tệp>`:**  Xóa tệp khỏi working directory và staging area.
* **`git mv <tên_tệp_cũ> <tên_tệp_mới>`:** Đổi tên tệp.

Đây là danh sách chi tiết các lệnh Git thường được sử dụng. 
Bạn có thể tham khảo thêm tài liệu chính thức của Git để tìm hiểu thêm về các lệnh nâng cao và chi tiết: [https://git-scm.com/docs](https://git-scm.com/docs)