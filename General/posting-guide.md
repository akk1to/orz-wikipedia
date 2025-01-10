---
icon: note
tags: [Hướng dẫn đăng bài, Guide]
---
# Hướng dẫn thêm trang mới cho ChuyentinORZ wiki
Trang wiki này sử dụng **Retype**, một bootstrap Wiki page, sử dụng **markdown format** để viết nội dung cho trang.<br>
Bài viết này sẽ hướng dẫn cách để viết một bài post hoàn chỉnh, từ cách viết file markdown tới cách post lên trang này.<br>
Vui lòng tham khảo cách để viết một file markdown hoàn chỉnh trên [markdownguide.org](https://markdownguide.org).
!!!
Bạn có thể xem file [posting-guide.md](https://github.com/akk1to/orz-wikipedia) để biết format của bài post này.
!!!
---
## Viết file markdown (.md)
Để bắt đầu, bạn cần phải viết một file markdown, có chứa nội dung của bài post bạn sẽ đăng. Dưới đây là một file mẫu `sample.md` đơn giản chỉ với tiêu đề và một hàng chữ.
```md
---
icon: {icon của bài viết}
tags: [tag của bài viết, ngăn cách bởi dấu ',']
---
# Tiêu đề bài viết

Đây là nội dung của bài viết
```
Chúng ta có thể viết lại file mẫu này một cách chỉn chu hơn, thêm các components cho bài viết như sau.
```md
---
icon: apps
tags: [application]
---
# Tiêu đề của bài viết

Đây là nội dung chính của bài viết.

## Đây là heading 2
### Đây là heading 3
#### Đây là heading 4
##### Đây là heading 5

Link dẫn tới [file nội bộ](README.md) và [trang web ngoài](https://example.com) đều hoạt động.

![ChuyentinORZ Favicon](logo.png)

Hàng chữ có **chữ đậm**, _chữ nghiêng_, ~~gạch ngang~~ và `code snippet`.

## Danh sách

- Số 1
- Số 2
- Số 3

1. Số 1
2. Số 2
3. Số 3

> "Nice! Đây là một câu quote!"

!!!
Cần chú ý điều gì đó? Đánh dấu nó bằng một cái cảnh báo!
!!!

+++ Tab 1
Đây là tab 1
+++ Tab 2
Đây là tab 2
```

!!!
Bạn có thể xem thử file mẫu trên [ở bài viết này](sample.md).
!!!

Hệ thống ChuyentinORZ Wiki sử dụng **Retype**, hỗ trợ nhiều components được thêm vào bài viết. Bạn có thể xem rõ các components trong bài viết (như là file download, embed, icon...) [thông qua link này (Retype Documentation)](https://retype.com/components/). Ở đây sẽ chỉ liệt kê một số components đáng chú ý, cần thiết cho wiki.

### Chú ý (Alert)
Ô chú ý giúp bạn có thể nhấn mạnh (highlight) một chú ý quan trọng cho người đọc.<br>
Để tạo một ô chú ý, các bạn chỉ cần thêm ba dấu `!` trước và sau nội dung cần thông báo.<br>
```md
!!!
Đây là một thông báo
!!!
```
!!!
Đây là một thông báo
!!!
Chi tiết vui lòng [tham khảo link sau (Retype Documentation)](https://retype.com/components/alert/).

### Bagde
Giống với nút, badge sử dụng chung syntax với hyperlink, nhưng được define thêm `!bagde`.
||| :icon-play: Demo
[!badge badge](https://example.com)<br>
[Normal link](https://example.com)
||| :icon-code: Source
```md
[!badge badge](https://example.com)
[Normal link](https://example.com)
```
|||
!!!
Chi tiết vui lòng [tham khảo link sau (Retype Documentation)](https://retype.com/components/badge/).
!!!
### Nút
Giống với Bagde, syntax của nút cũng giống với hyperlink, nhưng được define thêm `!button`.
||| :icon-play: Demo
[!button Link](https://example.com)<br>
[Normal link](https://example.com)
||| :icon-code: Source
```md
[!button Link](https://example.com)
[Normal link](https://example.com)
```
|||
!!!
Chi tiết vui lòng [tham khảo link sau (Retype Documentation)](https://retype.com/components/button/).
!!!
### Code block
Code block được sử dụng để chứa một đoạn code demo cho bài viết. Sử dụng 3 dấu "`" để define một ô CodeBlock
||| :icon-play: Demo
```cpp
#include<bits/stdc++.h>
using namespace std;

int main(){
    cout << "Hello world!\n";
    return 0;
}
```
||| :icon-code: Source
~~~
```cpp
#include<bits/stdc++.h>
using namespace std;

int main(){
    cout << "Hello world!\n";
    return 0;
}
```
~~~
|||

!!!
Chi tiết vui lòng [tham khảo link sau (Retype Documentation)](https://retype.com/components/code-block/).
!!!

Chi tiết toàn bộ các components, vui lòng tham khảo [thông qua link này (Retype Documentation)](https://retype.com/components/).