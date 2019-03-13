## Một số chức năng của VMware Workstation

**VMware Workstation** là một trong những phần mềm tạo máy tính ảo, nó có đầy đủ tính năng để tạo ra một chiếc máy tính ảo có khả năng làm việc giống 
hệt với máy tính thật.

### 1. Switch ảo (Virtual Switch)

Những  switch ảo hay còn gọi là mạng ảo, chúng có tên là VMnet0, VMnet1, VMnet2… một số switch ảo được gắn vào mạng một cách mặc định.
 Mặc định khi cài Wmware thì có sẵn 3 Switch ảo như sau: VMnet0 chế độ Bridged (cầu nối), VMnet8 chế độ NAT và VMnet1 chế độ Host-only. 

Muốn thêm bớt hoặc chỉnh các option 1 card mạng bằng cách vào **Edit** - > **Virtial Network Edittor**.

![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/1.png)

- **Chế độ Bridge** ở chế độ này thì card mạng trên máy ảo sẽ được gắn trực tiếp với card mạng vật lý, máy ảo sẽ kết nối internet thông 
qua lớp card mạng vật lý và có chung lớp mạng với card mạng vật lý.

- **Chế độ NAT** cho phép máy ảo đi internet thông qua cơ chế NAT (NAT device). Lúc này lớp mạng bên trong máy ảo khác hoàn toàn với lớp mạng của 
card vật lý bên ngoài. IP của card mạng sẽ được cấp bởi DHCP VMnet8 cấp, trong trường hợp muốn thiết lập IP tĩnh cho card mạng máy ảo bạn phải đảm bảo 
chung lớp mạng với VNnet8 thì máy ảo mới có thể đi internet.

- **Cơ chế Host-only** ở cơ chế này máy ảo được kết nối với VMnet có tính có tính năng Host-only(có thể add nhiều VMnet Host-only). 
VNnet Host-only kết nối ra một card mạng ảo tương ứng ngoài máy thật. Ở chế độ này máy ảo không có kết nối internet. 
IP của máy ảo được cấp bởi DHCP của VMnet tương ứng. 
Trong nhiều trường hợp đặc biệt cần cấu hình riêng, ta có thể tắt DHCP trên VMnet và cấu hình IP bằng tay cho máy ảo.

### 2. Sửa dải IP của một Vmnet

![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/2.png)

### 3. Cấu hình DHCP cho VMware

DHCP (Dynamic Host Configuration) server ảo đảm nhiệm việc cung cấp địa chỉ IP cho các máy ảo trong việc kết nối máy ảo vào các Switch ảo 
không có tính năng Bridged (VMnet0).  DHCP  server ảo cấp phát địa chỉ IP cho các máy ảo có kết nối với VMnet Host-only và NAT.

![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/3.png)

### 4. LAN segment

Các card mạng của máy ảo có thể gắn kết với nhau thành từng LAN Segment. Không giống như VMnet, LAN Segment chỉ kết nối các máy ảo được gán trong một 
LAN Segment lại với nhau mà không có những tính năng như DHCP và LAN Segment không thể kết nối ra máy thật như các Virtual Switch VMnet.

![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/4.png)

### 5. Cách phân vùng khi cài đặt Ubuntu

Có 4 option để lựa chọn khi cài đặt 

-	**Erase disk install Ubuntu**: Tất cả dữa liệu trong hệ thống sẽ bị xóa
-	**Encrypt the new Ubuntu installation for security**: Bạn sẽ chọn khóa bảo mật trong bước tiếp theo
-	**Use LVM with the new Ubuntu installation** : Sử dụng kỹ thuật LVM 
-	**Something else**: Bạn có thể tạo hoặc thay đổi kích thước các partitions, hoặc chọn nhiều partitions 

![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/5.png)

### 6. Clone máy ảo trên VMware

**Clone** máy ảo được hiểu là tạo ra 1 nhân bản  máy ảo trước đó thành các bên giống hệt máy ảo ban đầu với mục đích tiết kiệm thời gian cho việc lặp đi lặp lại 
cài đặt các máy ảo có cấu hình giống nhau. 

Các bước clone 1 máy ảo bằng Vmware 

- Bước 1: Click chuột phải vào máy ảo muốn **Clone** --> **Manage** --> **Clone**
( Chú ý: Khi máy ảo đang bật thì quá trình clone không thực hiện được)

![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/Screenshot_1.png)

- Bước 2: Nhấn **Next**

![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/Screenshot_2.png)

- Bước 3: Trong hộp thoại **Clone from**, chọn  **The current state in the virtual machine** sau đó nhấn **Next**

![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/Screenshot_3.png)

- Bước 4: Trong phần **Clone method** có 2 lựa chọn:
	- **Create a linked clone**

Là bản sao của máy ảo mới nhưng ổ đĩa ảo này sử dụng là của máy ảo ban đầu, nghĩa là khi bạn thao tác trên máy ảo mới 
thì sẽ tác động tới máy ảo cha nó (ghi dữ liệu vào, xóa,...)

	- **Create a full clone**
Là bản sao máy ảo đầy đủ, tất cả các hình ảnh đĩa được chép vào ổ đĩa ảo mới (độc lập với máy ảo cha của nó). 
Các Clone này cũng hoạt động độc lập với cha của nó.

![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/Screenshot_4.png)

- Bước 5: Quá trình Clone đang diễn ra

![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/Screenshot_5.png)


![alt](https://github.com/chinguyen97/VMwareWorkstation-/blob/master/image/Screenshot_6.png)

Quá trình clone thành công!


