# AGX_Orin_install
update system time
sudo date -s "$(wget -qSO- --max-redirect=0 google.com 2>&1 | grep Date: | cut -d' ' -f5-8)Z"

eigen install 
https://blog.csdn.net/p942005405/article/details/100653731
