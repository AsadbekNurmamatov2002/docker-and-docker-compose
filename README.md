# Docker va Docker Compose, farqi nimada?
* Docker va Docker Compose o'rtasidagi farq nima? Nega bizga loyihada Dockerfile va docker-compose.yml fayli kerak?
__Javob:__
Docker bilan ishlashda ikkita tushuncha mavjud: Image va Container.

Tasvirlar bizning ilovamizni hisobga olgan holda maxsus tuzilgan faylda saqlangan mini operatsion tizimlarga o'xshaydi. Buni kompyuteringiz o'chirilgan paytda qattiq diskingizda o'tirgan maxsus operatsion tizim kabi tasavvur qiling.
Konteynerlar sizning rasmingiz namunalarini ishga tushiradi.


Tasavvur qiling-a, sizda umumiy qattiq disk (yoki eski maktab bo'lsangiz, hatto CD/DVD) bor edi, unda bir nechta mashinalarda ishlay oladigan operatsion tizim mavjud edi. Diskdagi fayllar "tasvir" va mashinada ishlaydigan fayllar "konteyner" dir.

Docker shunday ishlaydi, sizda mashinada tasvir deb nomlanuvchi fayllar mavjud va bu fayllarning ishlayotgan namunalari konteyner deb ataladi. Tasvirlar boshqa foydalanuvchilar uchun ham yuklab olishlari va o'z mashinalarida ishlashi uchun yuklanishi va baham ko'rilishi mumkin.

Bu bizni Docker vs Docker Compose ga olib keladi.

Docker - bu tasvirlarni boshqaradigan (yaraydigan, saqlaydigan yoki baham ko'radigan) va konteynerlarni ishga tushiradigan asosiy texnologiya.

Biz Docker faylini Dockerga tasvirlarimizni qanday yaratishni aytib beramiz. Misol uchun, biz aytamiz: Python 3 asosiy tasviridan boshlanadi, keyin ushbu talablarni o'rnatadi, keyin bu papkalarni yaratadi, so'ngra ushbu foydalanuvchiga o'ting va hokazo... (Men amaldagi qadamlarni haddan tashqari soddalashtiryapman, lekin bu faqat fikrni tushuntirish uchun) .


Buni amalga oshirganimizdan so'ng, biz docker build-ni ishga tushirish orqali Docker yordamida rasm yaratishimiz mumkin.. Agar buni ishga tushirsangiz, Docker bizning Dockerfile-dagi har bir qadamni bajaradi va natijani tizimda tasvir sifatida saqlaydi.

Tasvir yaratilgandan so'ng, uni quyidagi kabi qo'lda ishlatishingiz mumkin:

>      docker run <image_id>

Ammo, agar siz hajmlarni sozlashingiz kerak bo'lsa, ularni quyidagicha ishga tushirishingiz kerak:

Ko'pincha ilovalarni ishga tushirish uchun bir nechta rasm kerak bo'ladi. Misol uchun, sizda ilova va ma'lumotlar bazasi bo'lishi mumkin, shuningdek, ular o'rtasida tarmoqlar va umumiy hajmlarni sozlashingiz kerak bo'lishi mumkin.

Shunday qilib, har safar xizmatni ishga tushirishni xohlaganingizda, ishga tushirmoqchi bo'lgan har bir konteyner uchun tegishli konfiguratsiyalar va identifikatorlar bilan yuqoridagi buyruqlarni yozishingiz kerak bo'ladi ...

Siz kutganingizdek, bu murakkab, zerikarli va tezda boshqarish qiyin bo'lishi mumkin ...

Bu erda Docker Compose keladi ...

Docker Compose - bu Docker bizning tasvirlarimizni kodimiz bilan saqlanishi va qayta ishlatilishi mumkin bo'lgan yaml faylida qanday ishlashini aniqlash uchun ishlatiladigan vositadir.

Shunday qilib, agar biz ilova tasvirimizni konteyner sifatida ishga tushirishimiz, 8000 portini almashishimiz va hajmni xaritalashimiz kerak bo'lsa, buni qilishimiz mumkin:

>      docker run -v /path/to/vol:/path/to/vol -p 8000:8000 <IMAGE_ID>
