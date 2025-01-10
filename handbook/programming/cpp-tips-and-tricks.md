---
icon: light-bulb
tags: [C++, CPP, Competitive Programming, tips & tricks, mẹo lập trình thi đấu]
order: 10
---
# Mẹo lập trình thi đấu C++
Dưới đây là một số mẹo cho C++ trong lập trình thi đấu.
## Fast I/O
Trong hầu hết các bài nộp C++, ta thường bắt gặp **2 dòng lệnh phổ biến ở đầu hàm `main`**:
```C++
ios_base::sync_with_stdio(false);
cin.tie(NULL);
```
2 câu lệnh này giúp **tăng tốc chương trình** bằng cách thay đổi cách nhập xuất của nó.
- `ios_base::sync_with_stdio(false)` tắt đồng bộ giữa cách nhập xuất của C và C++. Tính năng này giúp ta có thể sử dụng linh hoạt giữa hai cách nhập xuất khác nhau. Khi tắt tính năng này, chương trình của ta sẽ chạy nhanh hơn nếu bài toán yêu cầu nhập xuất dữ liệu nhiều lần. Lưu ý rằng nếu tắt đồng bộ thì không nên sử dụng đồng thời **2** cách nhập xuất.
- `cin.tie(NULL)` tắt  đồng bộ giữa `cin` và `cout`. `tie()` được dùng để đảm bảo tất cả các dữ liệu của `cout` sẽ được xuất ra màn hình trước khi thực hiện `cin` nhập dữ liệu. Điều này sẽ giúp ích cho các chương trình cần sự tương tác giữa người và chương trình, hoặc chương trình và chương trình - thứ mà ngoài dạng bài toán tương tác ra thì không cần thiết trong lập trình thi đấu. Việc tương tác này sẽ chương trình của ta sẽ chạy chậm đi. Ta tắt tính năng này để gia tăng tốc độ chương trình.

## Sử dụng `'\n'` thay thế cho `endl`
Trong lập trình thi đấu, sẽ tốt hơn nếu ta sử dụng `'\n'` để xuống dòng thay vì sử dụng `endl`.<br>
Ta có thể hiểu `endl` giống như khi ta viết `'\n' << flush`.<br>
`flush` là thao tác đẩy dữ liệu từ bộ đệm đầu ra (output buffer) ra thiết bị đầu ra. Nói cách khác, nó đảm bảo rằng tất cả dữ liệu đang chờ trong bộ đệm sẽ được ghi ra màn hình.<br>
Khi `flush` thường xuyên sẽ giảm hiệu suất của ta, việc dùng`'\n'` để xuống dòng trong các chương trình sẽ cho ta tốc độ chạy code nhanh hơn so với việc sử dụng `endl`.
## Rút gọn code
### Type name
Ta có thể dùng `typedef` để rút gọn chương trình của ta.<br>
VD:

```c++
typedef long long ll;
```
Sẽ giúp làm ngắn code:
```c++
long long a = 123456;
long long b = 246802;
cout << a + b << "\n";
```
thành:
```c++
ll a = 123456;
ll b = 246802;
cout << a + b << "\n";
```

### Macros
Macro thay đổi kí tự hoặc xâu kí tự trong mã (code) khi biên dịch chương trình.<br>
Trong C++ macro được định nghĩa bằng `#define {Tên_macro} {macro}`.<br>
VD: 

```c++
#define ll long long // macro cho kiểu dữ liệu
#define PI 3.14159 // macro cho một số
#define REP(i, a, b) for (int i = a; i <= b; ++i) //Macro cho một câu lệnh lặp
```

### Xuống dòng
Dưới đây là một đoạn của một chương trình in ra các giá trị của một mảng \\(2\\) chiều kích thước `n * m`:
```C++
for (int i = 1; i <= n; ++i) {
	for (int j = 1; j <= m; ++j) {
		cout << a[i][j] << ' ';
	}
	cout << '\n';
}
```
Thay vì phải in thêm một câu lệnh cout sau mỗi lần in xong một hàng, ta có cách viết khác:
```C++
for (int i = 1; i <= n; ++i) {
	for (int j = 1; j <= m; ++j) {
		cout << a[i][j] << "\n "[j < m];
	}
}
```
Dòng lệnh này có ý nghĩa: `"\n "` là một xâu kí tự, trong khi ta chưa duyệt đến phần tử cuối cùng, điều kiện `j < m` thỏa mãn, chương trình in ra kí tự vị trí 1 của xâu: `' '` - dấu cách. Khi đã duyệt đến phần tử cuối cùng, điều kiện `j < m` không thỏa mãn, chương trình in ra kí tự vị trí 0 của xâu: `'\n'` - xuống dòng.

## Viết số lớn
Sẽ có nhiều bài yêu cầu ta phải tạo một mảng lớn (như 10^6^ chẳng hạn), nhiều người có thể sẽ viết một mảng `a` và số 10^6^ cộng thêm một số nhỏ như 10: `a[1000010]`. Kiểu viết này tuy không sai nhưng rất dễ xảy ra lỗi.

```C++
/*
Cách viết này rất dễ sai vì rất dễ viết nhầm
VD:
a[1000010] nhưng lại viết thành a[10000010]
*/
int a[1000010], b[1000010], c[1000010];  
int d[1000010], e[1000010], f[1000010];
```

Đồng thời, khi sửa lại kích thước mảng cũng rất khó khăn khi ta phải sửa lại tất cả các số ấy. Nếu ta muốn đổi kích thước của các mảng ví dụ trên thì ta viết lại 6 lần!<br>
Ta tạo một hằng số `N` tượng trưng cho kích thước của mảng. Ta cho `N = 1e6 + 10` với giá trị bằng `1000010`, vừa dễ nhìn vừa khó mắc lỗi, đồng thời cũng dễ sửa hơn.

```C++
const int N = 1e6 + 10;
int a[N], b[N], c[N];
int d[N], e[N], f[N];
```
Chữ `e` (hoặc `E`) trong đoạn code là [E notation](https://en.wikipedia.org/wiki/Scientific_notation#E_notation). Khi viết mEn sẽ có giá trị: m × n^10^.<br>
VD: 
- `1e6 = 10^6 = 1000000`
- `2e5 = 2 * 10^5 = 200000`

## Câu lệnh rẽ nhánh trong một dòng
Có những lần bạn phải gán giá trị theo từng trường hợp:
```C++
\\ tìm số lớn nhất trong hai số
int a, b;
int ans;
if(a < b) ans = b;
else ans = a;
```
Ta có thể rút gọn lại thành:
```C++
int a, b;
int ans = a < b ? b : a;
```

## For auto 
!!! warning
Mẹo chỉ áp dụng với tiêu chuẩn C++17.
!!!
Giả sử ta có một `vector` chứa `pair`, và ta muốn in ra các giá trị của từng `pair` trong vector, ta làm như sau:
```C++
vector<pair<int, int>> arr = {{1, 2}, {3, 4}, {5, 6}};
for(auto x : arr){
	cout << x.first << ' ' << x.second << '\n';
} 
```
Thay vào đó, ta có thể viết theo cách khác:
```C++
for(auto [x, y] : arr){
	cout << x << ' ' << y << '\n';
}
```
## Khai báo hàm ở dưới hàm `main()`
!!! info
Xin nói trước rằng đây không hẳn là một mẹo và nói đúng hơn thì nó là một sở thích cá nhân khi viết code lập trình thi đấu của tác giả.
!!!
Các chương trình C++ khi khai báo các chương trình con thường sẽ viết như sau:
```C++
#include <bits/stdc++.h>
#define ll long long
using namespace std;

void foo(){
	[...]
}

int main () {
	foo();
	
	return 0;
}
```
Ta cũng có thể khai báo theo cách khác:
```C++
#include <bits/stdc++.h>
#define ll long long
using namespace std;

void foo();

int main () {
	foo();
	
	return 0;
}

void foo(){
	[...]
}
```
Tại sao lại khai báo hàm dưới hàm `main()`?<br>
Ta có một số lợi ích khi khai báo hàm theo cách này:<br>
**Lợi ích 1:** Dễ phân tích code.<br>
Với cách viết này, ta có thể phân tích code từ trên xuống một cách dễ dàng: Ta biết được các hàm có trong chương trình ở ngay đầu chương trình một cách ngắn gọn (mỗi dòng 1 hàm), biết được các hàm được sử dụng như thế nào trong hàm `main()` ngay sau đó, và biết cách hoạt động của các hàm ở cuối chương trình. Còn cách viết ở trên thì ta phải lướt lên lướt xuống để làm được những điều tương tự.<br>
**Lợi ích 2:** Không xuất hiện lỗi khi có các hàm phụ thuộc lẫn nhau.<br>
Ta có chương trình sau:
```C++
#include <bits/stdc++.h>
#define ll long long
using namespace std;

bool odd(int x){
	if(x == 0) return 0;
	if(x == 1) return 1;
	return even(x - 1);
}

bool even(int x){
	if(x == 0) return 1;
	if(x == 1) return 0;
	return odd(x - 1);
}

int main() {
	cout << odd(5);
	return 0;
}
```

Chương trình ở trên sẽ không chạy được do hàm `odd()` được khai báo trước hàm `even()`, từ đó "không thấy" hàm ấy.<br>
Vẫn đề đó sẽ không tồn tại nếu ta viết theo cách sau:

```C++
#include <bits/stdc++.h>
#define ll long long
using namespace std;

bool odd(int x);
bool even(int x);

int main() {
	cout << odd(5);
	return 0;
}

bool odd(int x){
	if(x == 0) return 0;
	if(x == 1) return 1;
	return even(x - 1);
}

bool even(int x){
	if(x == 0) return 1;
	if(x == 1) return 0;
	return odd(x - 1);
}
```

Bằng cách khai báo các hàm ở dưới hàm main, ta tránh được lỗi xảy ra khi các hàm phụ thuộc lẫn nhau.<br>
Tuy nhiên, cách viết này cũng tồn tại một vài bất lợi, cụ thể là khi sửa các hàm ta phải sửa tận **2 vị trí** thay vì 1.