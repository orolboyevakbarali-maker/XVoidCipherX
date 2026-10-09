# Meni birinchi proyektim. Bu Network ga asoslangan bo`lib, virtual boxda o`rnatib oldim.

![Screenshot From 2026-09-29 10-01-10.png](Meni%20birinchi%20proyektim%20Bu%20Network%20ga%20asoslangan%20b/Screenshot_From_2026-09-29_10-01-10.png)

Biz ochganimizda shunday oyna ochildi. Men berilgan ip address dan foydalanib, kali terminalida tekshirdim.

```jsx
nmap 10.0.2.15
```

![Screenshot From 2026-09-30 19-57-55.png](Meni%20birinchi%20proyektim%20Bu%20Network%20ga%20asoslangan%20b/Screenshot_From_2026-09-30_19-57-55.png)

Bundan biz ko`rishimiz mumkin 4 ta port mavjudligini. Bularni 22, 80, 2222 va 8080. Men ularni googleda ochib ko`rdim.Keyin men 3 ta port ichida hech nima chiqmadi, ular 22, 80, 8080 portlari.

![Screenshot From 2026-09-29 10-14-22.png](Meni%20birinchi%20proyektim%20Bu%20Network%20ga%20asoslangan%20b/Screenshot_From_2026-09-29_10-14-22.png)

Menda faqat 2222 portni ko`rish qoldi. Uni men gobusterda ham tekshirdim.

```jsx
gobuster dir -u http://10.217.222.213 -w /usr/share/wordlists/dirb/commom.txt
```

![Screenshot From 2026-09-29 10-12-58.png](Meni%20birinchi%20proyektim%20Bu%20Network%20ga%20asoslangan%20b/Screenshot_From_2026-09-29_10-12-58.png)

Keyin men 10.217.222.213:2222 portni kali terminalida tekshirdim.

```jsx
nc 10.217.222.213 2222
```

![Screenshot From 2026-09-29 10-20-20.png](Meni%20birinchi%20proyektim%20Bu%20Network%20ga%20asoslangan%20b/Screenshot_From_2026-09-29_10-20-20.png)

#### Keyin men berilgan ip address ga qo`shimcha tarzda **ls** buyrug`ini qo`shganimda ichida **user.txt** fayl bor ekanligini ko`rdim.

```jsx
cat user.txt
```

![Screenshot From 2026-09-30 20-08-08.png](Meni%20birinchi%20proyektim%20Bu%20Network%20ga%20asoslangan%20b/Screenshot_From_2026-09-30_20-08-08.png)

Men bu faylni ko`rish uchun revshells saytdan foydalandim.

![Screenshot From 2026-09-30 10-03-12.png](Meni%20birinchi%20proyektim%20Bu%20Network%20ga%20asoslangan%20b/Screenshot_From_2026-09-30_10-03-12.png)

Bu orqali men tizimga login parolsiz kirib oldim. Endigi maqsad root ni egallash. 

![Screenshot From 2026-09-30 19-27-05.png](Meni%20birinchi%20proyektim%20Bu%20Network%20ga%20asoslangan%20b/Screenshot_From_2026-09-30_19-27-05.png)

Rootga kirish uchun men [https://gtfobins.org/](https://gtfobins.org/) saytidan foydalanib egallab oldim. keyingi maqsad parolini men bilgan parollanga o`zgartirish edi.

![Screenshot From 2026-09-30 19-45-20.png](Meni%20birinchi%20proyektim%20Bu%20Network%20ga%20asoslangan%20b/Screenshot_From_2026-09-30_19-45-20.png)

So`ngi flag ni cat root.txt orqali ko`rdim.

```jsx
cat root.txt
```