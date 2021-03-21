**This tutorial teatch you how the computer with macos can link to the computer with linux .**

## Reference 

* https://mofanpy.com/tutorials/others/linux-basic/

## Requirement

* Macbook Pro catalina
* Unbuntu 18.04

# SSH

## Steps

1. Run ```sudo apt-get install openssh-server``` in your computer with linux
2. Run ``ifconfig`` to observe your IP dress of the computer with linux
3. Open a new termial on your computer MacBook Pro and run ```ssh username@IP_adress```

<img src="Fig.assets/截屏2021-03-21 17.35.48.png" alt="截屏2021-03-21 17.35.48" style="zoom:50%;" />

# VNC

## Stpes

1. Open a termial and run ```sudo apt-get install x11vnc``` on your computer with linux 
2. Run ```x11vnc -storepasswd``` and set your password
3. Run ```x11vnc -forever -shared -rfbauth ~/.vnc/passwd```
4. Run ``ifconfig`` to observe your IP dress of the computer with linux
5. Open screen sharing app on your MacBook Pro and type IP adress of the computer with linux and the password.

