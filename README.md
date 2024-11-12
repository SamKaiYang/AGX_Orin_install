# AGX_Orin_install
### update system time (have network)
sudo date -s "$(wget -qSO- --max-redirect=0 google.com 2>&1 | grep Date: | cut -d' ' -f5-8)Z"


### update system time (haven't network)
sudo date -s 2024-11-12
sudo date -s 13:27:55
eigen install 
https://blog.csdn.net/p942005405/article/details/100653731
