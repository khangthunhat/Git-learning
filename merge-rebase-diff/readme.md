## Tình Huống Ví Dụ: Xử Lý Conflict Khi Dùng `git merge` và `git rebase`

**Tình huống:**

Bạn đang phát triển tính năng mới trên branch `feature/new-login` và đồng nghiệp của bạn đang sửa lỗi trên branch `hotfix/bug-123`. Cả hai bạn đều cần thay đổi cùng một dòng code trong tệp `login.js`.

**1. Sử dụng `git merge`:**

1. **Đồng nghiệp merge `hotfix/bug-123` vào `main`:**
   ```
   git checkout main
   git merge hotfix/bug-123 
   git push origin main
   ```

2. **Bạn merge `main` vào `feature/new-login`:**
   ```
   git checkout feature/new-login
   git merge main
   ```

   Lúc này, Git phát hiện conflict vì cùng một dòng code đã được thay đổi trên cả hai branch. 

3. **Giải quyết conflict:**
   * Mở tệp `login.js`, bạn sẽ thấy các dấu hiệu conflict như sau:
     ```javascript
     <<<<<<< HEAD
     // Code của bạn trên branch feature/new-login
     =======
     // Code của đồng nghiệp trên branch hotfix/bug-123
     >>>>>>> main
     ```
   * Chọn giữ lại code của bạn, code của đồng nghiệp, hoặc kết hợp cả hai.
   * Xóa các dấu hiệu conflict (`<<<<<<<`, `=======`, `>>>>>>>`).
   * Lưu thay đổi.

4. **Kết thúc merge:**
   ```
   git add login.js
   git commit -m "Merge branch 'main' into feature/new-login"
   ```

**2. Sử dụng `git rebase`:**

1. **Rebase `feature/new-login` lên `main`:**
   ```
   git checkout feature/new-login
   git rebase main
   ```

   Git sẽ áp dụng từng commit của bạn lên trên commit mới nhất của `main`, và có thể gặp conflict tại commit bạn và đồng nghiệp cùng thay đổi `login.js`.

2. **Giải quyết conflict (tương tự như với `git merge`):**
   * Sửa conflict trong tệp `login.js`.
   * Lưu thay đổi.

3. **Tiếp tục rebase:**
   ```
   git add login.js
   git rebase --continue
   ```

4. **Đẩy thay đổi lên remote (lưu ý force push vì lịch sử branch đã thay đổi):**
   ```
   git push -f origin feature/new-login
   ```

**So sánh:**

* **`git merge`**: Giữ nguyên lịch sử của cả hai branch, tạo merge commit khi hợp nhất. Dễ hiểu và sử dụng, nhưng có thể tạo ra lịch sử phức tạp nếu có nhiều branch và merge thường xuyên.
* **`git rebase`**:  Tạo lịch sử tuyến tính, dễ theo dõi bằng cách "viết lại" lịch sử của branch hiện tại. Tuy nhiên, cần thận trọng khi sử dụng, đặc biệt là khi làm việc với branch đã được chia sẻ với người khác.

**Kết luận:**

Lựa chọn `git merge` hoặc `git rebase` phụ thuộc vào tình huống cụ thể và cách bạn muốn quản lý lịch sử branch. Điều quan trọng là hiểu rõ cách thức hoạt động của từng lệnh và cách giải quyết conflict khi chúng xảy ra. 
