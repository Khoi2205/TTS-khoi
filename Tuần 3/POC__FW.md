- [1. Thực hiện kiểm tra tính năng IPS](#1-thực-hiện-kiểm-tra-tính-năng-ips)
  - [2.1. Kịch bản](#21-kịch-bản)
- [3. IP reputation](#3-ip-reputation)
  - [3.1. Kịch bản](#31-kịch-bản)
- [4. Anti DDOS](#4-anti-ddos)
  - [4.1. Kịch bản](#41-kịch-bản)
- [5. Tính năng URL Filtering](#5-tính-năng-url-filtering)
  - [5.1. Kịch bản](#51-kịch-bản)
- [6. L7 App Control](#6-l7-app-control)
  - [6.1. Kịch bản](#61-kịch-bản)
- [7. Tính năng QoS](#7-tính-năng-qos)
  - [7.1. kịch bản](#71-kịch-bản)
- [8. SSL VPN Remote access](#8-ssl-vpn-remote-access)
  - [Kịch bản](#kịch-bản)





### 1. Thực hiện kiểm tra tính năng IPS 

2. Mô hình 

![Alt text](./anh_lab_3/image-3.png)

#### 2.1. Kịch bản 

```
Yêu cầu Thực hiện cài LAMP + wordpress trên centOS7
Thực hiện chèn file mã độc vào web 
Kết nối máy tính với thiết bị IPS.
Cấu hình fw  IPS để phát hiện và ngăn chặn các cuộc tấn công
Kiểm tra nhật ký của firewall IPS để xác minh rằng cuộc tấn công đã được phát hiện và ngăn chặn.
```




![Alt text](./anh_lab_3/image-2.png)





**Cấu hình trên policy**



![Alt text](./anh_lab_3/image-4.png)




**Cấu hình IPS dựa trên zone**


![Alt text](./anh_lab_3/image-5.png)



![Alt text](./anh_lab_3/image-6.png)




**Từ máy Windowns truy cập vào web server máy 192.168.202.40 và tải file mã độc về**


![Alt text](./anh_lab_3/image-1.png)




**Kiểm tra khả năng phát hiện trên Firewall khi bật tính năng IPS.**


![Alt text](./anh_lab_3/image-7.png)


![Alt text](./anh_lab_3/image-8.png)


![Alt text](./anh_lab_3/image-9.png)




### 3. IP reputation


#### 3.1. Kịch bản

```
Trên Firewall cấu hình tính năng IP reputation, không cho kết nối từ hệ thống đến IP độc hại 192.168.202.40 
Kiểm tra window(192.168.11.50 ) truy cập 192.168.202.40

```



Cấu hình Firewall:



![Alt text](./anh_lab_3/image-10.png)


**Kết quả trên window 7 không vào được dịch vụ gì của server**



![Alt text](./anh_lab_3/image-11.png)



Trên fw được cảnh báo về  truy cập 



![Alt text](./anh_lab_3/image-12.png)



### 4. Anti DDOS

![Alt text](./anh_lab_3/image-18.png)



#### 4.1. Kịch bản
```
Cấu hình chống anti ddos trên fw 
Thực hiện tấn công ddos bằng tool trên kali
Thực hiện dùng máy win 7 check xem khi đang tấn công thì sẽ như thế nào 
Thực hiện check log đẩy về trên fw
```


**Thực hiện kiểm tra vào web trên wwin 7***


![Alt text](./anh_lab_3/image-14.png)



**Thực hiện cấu hình trên fw**
```
Từ Tab Network => Zone => Tích chọn Zone untrust => Tích chọn Edit
Cửa sổ mới hiện ra => chọn tab Threat `Protection => Tích chọn checkbox Attack Defense => Chọn Configure

```

![Alt text](./anh_lab_3/image-20.png)



![Alt text](./anh_lab_3/image-19.png)





![Alt text](./anh_lab_3/image-21.png)



![Alt text](./anh_lab_3/image-22.png)




**Thực hiện tấn công trên máy kali**

`sử dụng tool pentmenu và hping3`


![Alt text](./anh_lab_3/image-16.png)




![Alt text](./anh_lab_3/image-17.png)




![Alt text](./anh_lab_3/image-13.png)



**Kết quả log đẩy về trên fw**


![Alt text](./anh_lab_3/image-15.png)


`Khi máy kali đang tấn công thì sử dụng máy win 7 vẫn có thể vào được trang web`



![Alt text](./anh_lab_3/image-23.png)



### 5. Tính năng URL Filtering


![Alt text](./anh_lab_3/image-39.png)


#### 5.1. Kịch bản 

```
Thực hiện ngăn chặn không cho truy cập vào các trang web 
Thực hiện cấu hình trên fw
Xem log đẩy về trên fw 

```

**Trước khi chặn** 

![Alt text](./anh_lab_3/image-34.png)



![Alt text](./anh_lab_3/image-29.png)



**Cấu hình trên fw**





![Alt text](./anh_lab_3/image-25.png)






![Alt text](./anh_lab_3/image-27.png)




![Alt text](./anh_lab_3/image-33.png)


`Cấu hình dns trên mô hìn như sau`



![Alt text](./anh_lab_3/image-37.png)



![Alt text](./anh_lab_3/image-38.png)



**Bật tính năng URL Filtering trong policy.**




**Kết quả sau khi chặn**



![Alt text](./anh_lab_3/image-24.png)




![Alt text](./anh_lab_3/image-30.png)



![Alt text](./anh_lab_3/image-31.png)


**Xem log về fw cảnh báo về**



![Alt text](./anh_lab_3/image-32.png)



### 6. L7 App Control


#### 6.1. Kịch bản

```
Cấu hình chặn không cho kết nối với app trên pc 
Thực hiện show kết quả sau khi cấu hình 


```
**Trước khi chưa cấu hình chặn** 



![Alt text](./anh_lab_3/image-40.png)



**Thực hiện cấu hình POC trên fw**


![Alt text](./anh_lab_3/image-41.png)



**Sau khi cấu hình chặn**


![Alt text](./anh_lab_3/image-35.png)



### 7. Tính năng QoS


Mô hình 


![Alt text](./anh_lab_3/image-42.png)



####  7.1. kịch bản




```
Trên tường lửa, tạo một chính sách QoS mới.
Cấu hình police trên fw 
Xem log trên fw
```



Cấu hình trên fw : 


![Alt text](./anh_lab_3/image-43.png)


![Alt text](./anh_lab_3/image-44.png)


![Alt text](./anh_lab_3/image-45.png)


![Alt text](./anh_lab_3/image-46.png)


**Thực hiện tải file win7 về**


![Alt text](./anh_lab_3/image-47.png)



**Thực hiện xem kết quả trên fw**


![Alt text](./anh_lab_3/image-48.png)



### 8. SSL VPN Remote access


![Alt text](./anh_lab_3/image-57.png)


#### Kịch bản 

```
Cấu hình tính năng VPN Remote Access và tạo các user cho phép remote access trên Firewall.
-	Trên Security Policy : chọn user cho từng policy đi vào từng vùng mạng khác nhau.
-	Thực hiện remote access kiểm tra.

```


**Thực hiện cấu hình trên fw**


![Alt text](./anh_lab_3/image-49.png)



![Alt text](./anh_lab_3/image-50.png)



![Alt text](./anh_lab_3/image-51.png)


![Alt text](./anh_lab_3/image-60.png)



```
Trong Security policy, chọn user cho từng policy đi vào từng vùng mạng khác nhau.
```


![Alt text](./anh_lab_3/image-59.png)


![Alt text](./anh_lab_3/image-58.png)




**Thực hiện truy cập vào window để truy tải vpn về**


![Alt text](./anh_lab_3/image-53.png)


![Alt text](./anh_lab_3/image-55.png)



