# AGX_Orin_install
### update system time (have network)
sudo date -s "$(wget -qSO- --max-redirect=0 google.com 2>&1 | grep Date: | cut -d' ' -f5-8)Z"


### update system time (haven't network)
sudo date -s 2024-11-12
sudo date -s 13:27:55
eigen install 
https://blog.csdn.net/p942005405/article/details/100653731

# AGX_Orin_image_install
### wsl 安裝在非系統槽
https://hackmd.io/@Kuihao/wsl
### use windows wsl
https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps
https://docs.nvidia.com/sdk-manager/wsl-systems/index.html
https://learn.microsoft.com/en-us/windows/wsl/connect-usb
https://blog.csdn.net/weixin_43854380/article/details/126584835

usbipd attach --wsl --busid <busid> –-auto-attach

