# ThinkPad E14 Gen5 Enable fprint on Arch Linux

<p align="center">
  <img src="https://mir-s3-cdn-cf.behance.net/project_modules/1400_opt_1/091089194042773.661d38a331980.gif" alt="Banner animado" width="600" height="300" />
</p>

* Created by me **GABRIEL JESUS**
* Created for my personal use.
* If you'd like to follow the step-by-step instructions for installing biometrics, feel free to do so
* **I am not responsible for any errors or damages.**


## 1 - How to enable fingerprint:

### 1 - Install packages:
* Install fprintd and imagemagick:

    ```
    sudo pacman -S fprintd imagemagick
    ```

### 2 - Configuration:

* You can choose any editor you prefer to configure. Ex.: nano, vim, vi

  ```
  sudo vim /etc/pam.d/system-local-login
  ```

* Add **pam_fprintd.so** as sufficient to the **top of the auth section** of /etc/pam.d/system-local-login:

  ```
   auth		sufficient  	pam_unix.so try_first_pass likeauth nullok
   auth      sufficient pam_fprintd.so 
   auth      include   system-login
  ```


### 3 - Create fingerprint signature

* When typing the command **fprintd-enroll $user** you will enter the user's password and then place your finger on the biometrics to register.

  ```
  fprintd-enroll $user
  ```
  
* To verify the newly created fingerprint, use: 

   ```
    fprintd-verify
   ```

### 4 - Configuring GDM (gnome) to receive biometrics

  ```
  sudo usermod -aG group $username
  ```

* Now just configure it in the gnome settings menu
