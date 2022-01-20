# X-UI cPanel

Bảng điều khiển `xray` đa giao thức và nhiều người dùng việt hóa từ phiên bản China


# Tính năng

- Giám sát tình trạng hệ thống
- Hỗ trợ đa người dùng và đa giao thức
- Giao thức được hỗ trợ：vmess、vless、trojan、shadowsocks、dokodemo-door、socks、http
- Hỗ trợ cấu hình nhiều cấu hình đường truyền
- Thống kê lưu lượng, giới hạn lưu lượng, giới hạn thời gian hết hạn 
- Cấu hình xray có thể tùy chỉnh 
- Truy cập bảng điều khiển giao thức https (Chứng chỉ ssl tên miền của riêng bạn) 
- Đối với các mục cấu hình nâng cao hơn, hãy xem bảng điều khiển để biết chi tiết 

# Cài đặt
```
bash <(curl -Ls https://raw.githubusercontent.com/min9802/x-ui/master/install.sh)
```
# Cài bằng tay
1. Clone repo
Clone repo này về máy với lệnh sau
```
https://github.com/Min9802/x-ui.git
```
2. Cài đặt
Đăng nhập với root
```
cd /root/
rm x-ui/ /usr/local/x-ui/ /usr/bin/x-ui -rf
tar zxvf x-ui-linux-amd64.tar.gz
chmod +x x-ui/x-ui x-ui/bin/xray-linux-* x-ui/x-ui.sh
cp x-ui/x-ui.sh /usr/bin/x-ui
cp -f x-ui/x-ui.service /etc/systemd/system/
mv x-ui/ /usr/local/
systemctl daemon-reload
systemctl enable x-ui
systemctl restart x-ui
```
# Cài với docker (Chưa việt hóa)
1. cài đặt docker
```
curl -fsSL https://get.docker.com | sh
```
2. Cài đặt x-ui
```
mkdir x-ui && cd x-ui
docker run -itd --network=host \
    -v $PWD/db/:/etc/x-ui/ \
    -v $PWD/cert/:/root/cert/ \
    --name x-ui --restart=unless-stopped \
    enwaiax/x-ui:latest
```
3. Build
```
docker build -t x-ui .
```
## Hệ điều hành được hỗ trợ cài đặt

- CentOS 7+
- Ubuntu 16+
- Debian 8+


## Di chuyển dữ liệu từ v2-UI sang X-UI

Trước tiên hãy cài đặt phiên bản mới nhất của x-ui trên máy chủ nơi v2-ui được cài đặt, sau đó sử dụng lệnh sau để di chuyển. Lệnh này sẽ di chuyển tất cả dữ liệu tài khoản gửi đến của v2-ui của máy sang x-ui, cấu hình cài đặt bảng điều khiển và tên người dùng và mật khẩu sẽ không di chuyển.

> Sau khi di chuyển thành công, vui lòng `đóng v2-ui` và `khởi động lại x-ui`, nếu không quá trình chuyển đến của v2-ui và đầu vào của x-ui sẽ gây ra xung đột cổng(port).
```
x-ui v2-ui
```

## Nguồn tác giả

=== Vaxilu ===

Github: https://github.com/vaxilu
