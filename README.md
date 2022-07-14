# 1.Tại branch develop và feature/test-01 [cùng lịch sử commit + code]
![img](./test01.png?raw=true "Image")

# 2.Tại branch develop, giả sử xuất hiện commit mới với thay đổi tại file testing.md với nội dung: "Commit from dev branch"


# 3.Tại branch feature/test-01, giả sử xuất hiện commit mới với thay đổi tại file testing.md với nội dung: "Commit from feature/test-01"

# 4.Ở đây, cả 2 branch là develop và feature/test-01 có thay đổi tại dòng 2 của file testing.md, nên sẽ có conflict

# 5.Lúc này, tại branch feature/test-01 ta sẽ tiến hành sử dụng rebase để fix conflict bằng câu lệnh:
- git pull --rebase origin develop

# 6.Nếu chúng ta không muốn rebase nữa, thì có thể chạy lệnh bên dưới, lệnh này sẽ hủy yêu cầu rebase
- git rebase --abort

# 7. Để hoàn thành rebase, chúng ta cần fix hết các conflict nếu có, ở đây sẽ fix conflict ở file testing.md, sau khi fix xong, sẽ tiến hành add file đã resolve conflict vào staged. Khi tất cả các conflict đã được fix hết, chúng ta sẽ đến bước kế tiếp bằng cách chạy lệnh
- git rebase --continue


# 8.Tiếp theo, chúng ta sẽ cần rewrite lại commit message bằng vi, nhấn i để bắt đầu mode edit message, esc để thoát khỏi mode edit, :wq để lưu message đã thay đổi và đóng vi
# Lúc này check lại lịch sử commit, ta sẽ thấy có cả commit từ dev và feature/test-01


# 9.Hoàn thành việc fix conflict, chúng ta sẽ cần push force thay đổi lên remote branch
- git push -f