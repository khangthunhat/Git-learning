Tình huống: Bạn và đồng nghiệp của bạn đang cùng phát triển một tính năng mới cho một ứng dụng. Mỗi người làm việc trên các nhánh riêng biệt, nhưng đồng thời cũng có những thay đổi quan trọng trên nhánh chính (main) mà nhóm đã thống nhất phải kết hợp trước khi hoàn tất tính năng. Cả git merge và git rebase đều có thể được dùng để giải quyết vấn đề này, nhưng chúng hoạt động khác nhau trong cách quản lý lịch sử commit.

1. Tạo dự án và nhánh chính

Đầu tiên, tạo ra một dự án và giả lập môi trường làm việc nhóm.

# Khởi tạo repository
mkdir collaborative-project
cd collaborative-project
git init

# Tạo file index.html
echo "<h1>Welcome to our app</h1>" > index.html
git add index.html
git commit -m "Initial commit"

2. Đồng nghiệp của bạn (Dev A) tạo nhánh feature-A

Dev A làm việc trên tính năng đầu tiên (feature-A):

# Dev A tạo nhánh feature-A
git checkout -b feature-A

# Dev A chỉnh sửa file index.html
echo "<p>Feature A: User login form</p>" >> index.html
git add index.html
git commit -m "Added user login form in feature-A"

3. Bạn tạo nhánh feature-B

Trong khi đó, bạn làm việc trên nhánh feature-B:

# Tạo nhánh feature-B
git checkout -b feature-B

# Bạn thêm tính năng cho trang
echo "<p>Feature B: User registration form</p>" >> index.html
git add index.html
git commit -m "Added user registration form in feature-B"

4. Thay đổi quan trọng trên nhánh main

Nhóm trưởng thông báo rằng một thay đổi quan trọng đã được đưa vào nhánh main và cần phải có trong cả hai nhánh tính năng.

git checkout main

# Nhóm trưởng thay đổi nội dung chính của trang
echo "<h1>Welcome to our app - Now with SSL!</h1>" > index.html
git add index.html
git commit -m "Updated header with SSL information"

5. So sánh git merge và git rebase

Sử dụng git merge:

Dev A quyết định dùng git merge để kết hợp các thay đổi từ main vào nhánh feature-A.

# Trên nhánh feature-A
git checkout feature-A

# Merge main vào feature-A
git merge main

Kết quả: git merge giữ lại cả hai lịch sử commit từ main và feature-A. Nếu có xung đột, Dev A sẽ khắc phục chúng giống như quy trình ở trên, sau đó tạo ra một commit merge mới.

Lịch sử của dự án khi dùng git merge sẽ có nhiều nhánh:

git log --oneline --graph

Bạn sẽ thấy một commit merge trộn các thay đổi từ main và feature-A, giữ nguyên tất cả commit từ hai nhánh.

Sử dụng git rebase:

Trong khi đó, bạn (Dev B) quyết định dùng git rebase để giữ lịch sử gọn gàng.

# Trên nhánh feature-B
git checkout feature-B

# Rebase với main
git rebase main

Kết quả: git rebase “chuyển” các commit từ feature-B lên trên cùng của nhánh main, tạo ra một lịch sử tuyến tính. Nếu có xung đột, bạn cũng sẽ cần giải quyết tương tự như khi merge, nhưng sau đó bạn sẽ tiếp tục rebase.

Lịch sử commit sau khi rebase sẽ không có commit merge, mà các commit từ feature-B sẽ xuất hiện sau commit từ main.

6. Sự khác nhau sau cùng

	•	Git merge: Bạn thấy rõ nhánh được tách ra và sau đó hợp nhất. Lịch sử của dự án bao gồm cả nhánh chính và nhánh tính năng. Điều này làm cho lịch sử dễ theo dõi hơn khi làm việc với nhiều nhánh, nhưng có thể làm lịch sử phức tạp.
	•	Git rebase: Lịch sử gọn gàng, tuyến tính hơn. Tất cả các commit từ nhánh tính năng của bạn được đặt lên trên các commit từ nhánh main. Điều này phù hợp nếu bạn muốn giữ lịch sử sạch sẽ, nhưng cần cẩn thận khi rebase nhánh đã được chia sẻ với người khác.

7. Kết luận thực tiễn

Bạn có thể tạo một cuộc thảo luận ngắn gọn về việc trong những tình huống nào nên sử dụng git merge hoặc git rebase:

	•	Sử dụng git merge khi bạn muốn bảo toàn lịch sử đầy đủ, bao gồm các nhánh khác nhau và quá trình phát triển.
	•	Sử dụng git rebase khi bạn muốn một lịch sử gọn gàng, nhưng phải cẩn thận để không xung đột khi nhiều người cùng làm việc trên nhánh đó.

Kết thúc

Kịch bản này giúp mô phỏng môi trường làm việc nhóm với nhiều nhánh tính năng, cho thấy cách xử lý xung đột và sự khác biệt rõ ràng giữa git merge và git rebase.