#

## НАСТРАИВАЕМ MANJARO LINUX KDE ДЛЯ ИГР 

[ТОЛЬКО ПОСЛЕ УСТАНОВКИ ДРАЙВЕРОВ]     [КАК УСТАНОВИТЬ ДРАЙВЕРА CMОТРИТЕ В ФАЙЛЕ M.I.F. KDE]

#### - ВСЕ НЕОБХОДИМЫЕ ПАКЕТЫ И БИБЛИОТЕКИ ДЛЯ ИГР И ПРИЛОЖЕНИЙ 

 ``` sudo pacman -Syu --needed freeglut glew lib32-alsa-lib lib32-alsa-plugins lib32-glu lib32-icu lib32-libdrm lib32-libelf lib32-libglvnd lib32-libice lib32-libpciaccess lib32-libsm lib32-libxdamage lib32-libxi lib32-libxml2 lib32-libxshmfence lib32-libxxf86vm lib32-llvm-libs lib32-lm_sensors lib32-mesa lib32-ncurses lib32-readline lib32-wayland mesa-demos zenity cabextract gnu-netcat icoutils lib32-acl lib32-fontconfig lib32-freetype2 lib32-gettext lib32-harfbuzz lib32-lcms2 lib32-libjpeg-turbo lib32-libnl lib32-libpcap lib32-libpng lib32-libtiff lib32-libusb lib32-libxcursor lib32-libxrandr lib32-libxrender lib32-libxss libutempter p7zip wxgtk-common wxgtk2 wxpython xbitmaps xorg-luit xorg-xmessage xterm samba lib32-libudev0-shim lib32-libgudev lib32-libpulse lib32-libldap lib32-libxml2 lib32-libpng lib32-giflib lib32-gnutls lib32-mpg123 vulkan-icd-loader lib32-vulkan-icd-loader lib32-libldap lib32-openal ``` 

- У кого видеокарта от NVIDIA и установлен проприетарный драйвер, но игры не могут определить аппаратное ускорение, то надо установить пакеты:

 ``` sudo pacman -Syu opencl-nvidia lib32-opencl-nvidia lib32-nvidia-utils ``` 


#### - Устанавливаем Vulkan

Nvidia:  ``` sudo pacman -S vulkan-icd-loader lib32-vulkan-icd-loader ``` 

AMD:  ``` sudo pacman -S vulkan-radeon lib32-vulkan-radeon vulkan-icd-loader lib32-vulkan-icd-loader ``` 

Intel:  ```  sudo pacman -S vulkan-intel lib32-vulkan-intel vulkan-icd-loader lib32-vulkan-icd-loader ``` 

#### - Установка Steam + GameMod от Feral Interactive

 ``` sudo pacman -S steam-manjaro game-devices-udev gamemode ``` 

#### - Установка Lutris + Wine

 ``` sudo pacman -S lutris wine wine-staging winetricks protontrics ```  

#

# Полный список игр из моей Steam библиотеки

#A 

## - Albion: Online [NATIVE]

- Нативный клиент под Линукс
- Игра работает идеально

## - Assassin's Creed [PROTON]

- DXVK c DirectX 9 
- Игра работает отлично на Proton 4.11-9

## - Assassin's Creed: Revelations [PROTON]

- Игра работает из коробки (последний тест на Proton 4.11-9)

## - Assassin's Creed: Origins [PROTON]	

- Игра работает из коробки (последний тест на Proton 4.11-9)
- Переодически слетает Uplay, требуется полная переустановка игры

#

#B 

## - Battlefield: Bad Company 2 [PROTON]

- Через DXVK игра работает замечательно
- Более 100FPS на GeForce 1050Ti
- Игра полностью на русском языке
	
#C 

## - Crysis [PROTON]

- DXVK c DirectX 11
- Игра работает отлично на Proton 4.11-10

## - Crysis 2: Maximum Edition [PROTON]

- DXVK c DirectX 11 
- Игра работает отлично на Proton 4.11-9
	
#D

## - DOOM [PROTON]

- DOOM запускается с пол пинка!
- Proton 4.11-10
- Графика очень плавная и стабильно держит 60FPS
 	
E 	
F 	

#G

## - GTA V [PROTON]

- Стабильные 60FPS и плавная картинка
- Онлайн-режим не доступен. После создания персонажа, игра вылетает 	

H 	
I 	
J 

#
	
#K 

## - KILLING FLOOR [PROTON]

- Нативная Killing Floor нативно работает, к сожалению, плохо ... Проблема со звуком, он идет с треском и небольшой задержкой
- Досточно игру запустить на последнем Proton 4.11-9 и тогда все работает отлично ...

#
	
L 	
M 

## - Medal of Honor: Airborne [PROTON]

- Все работает отлично на послденем Proton 4.10
- Игра задействует DXVK + Directx 9

## - Medal of Honor: Single Player [PROTON]

- Все работает отлично на последнем Proton 4.10
	
N 

## - Northgard [NATIVE]

- Полностью нативная игрушка под Линукс
- Стратиегия в стиле Age of Empires 2 и Empire Apart, только про викингов
- Работает отлично! Плавная и приятная графика 
- Полностью локализована, без русской озвучки (она не нужна - это стратегия)
	
O 	
P 	
Q 	
R 

#

## RESIDENT EVIL 2 [PROTON]

- Resident Evil 2 Remake изначально, не запускается с коробки
- Не хватает одной библиотеки mfplat.dll

Как заставить работать игру?

01. Клонируем репозиторий с GitHub из ссылки ниже

 ``` git clone https://github.com/z0z0z/mf-installcab.git ``` 

02. Далее запускаем скрипт из клона и обновляем наш prefix

 ``` WINEPREFIX="/home/ИМЯ_ПОЛЬЗОВАТЕЛЯ/.local/share/Steam/steamapps/compatdata/883710/pfx" ./install-mf-64.sh ``` 

03. После того как скрипт закончит, докидываем в папку с игрой  ``` mfplat.dll ```  (он лежит в папке с клоном в домашней папке)

- Запускаем игру и наслаждаемся! На моей 1050Ti выдает 60FPS 
	
#

S 	
T 

## - The Witcher 3: Wild Hunt [PROTON]

- Все работает просто шикарно с Proton 4.10
- Игра стабильно держит 60FPS

	
U 	
V 	
W 	
X 	
Y 	
Z

#
#
#

# ЧАСТО ЗАДАВАЕМЫЕ ВОПРОСЫ

#### - Легкое подтормаживание игры после запуска. Что это?

 ``` В начале большинства игр, могут быть легкие подтормаживания, они связаны с новой функцией Steam с кеширование шейдеров. Эту функцию можно отключить в настройках клиента, но если поиграть в игру 10-15%, то это значительно улучшить общую производительность игры в дальнейшем! Вообщем, на ваш выбор! Лично я, эту функцию оставляю включенной. ``` 

#### - Проблемы с управлением?! 

 ``` В 90% случаев, когда есть проблемы с управлением — достаточно включить английскую раскладку в системе по умолчанию. Но если теряется фокус при нажатии на клавишу Alt, то самый простой способ — это смена клавиш переключения раскладки с Alt + Shift на Ctrl + Shift ``` 

#### - Проблемы со звуком?!

- Попробуйте отредактировать настройки звукового сервера (системные, а не WINE) 

 ``` sudo gedit /etc/pulse/default.pa ``` 

PS: Если в данном файле вы не нашли нужных параметров, то они значит, есть в файле:

 ``` sudo gedit /etc/pulse/daemon.conf ``` 

- Там находим строки и меняем их значения:

 ``` default-fragments = 5 ``` 

 ``` default-fragment-size-msec = 2 ``` 

После чего перезапускаем пульс:  ``` pulseaudio -k ``` 

- Все! Теперь вайн и звуковой сервер Pulse должны дружить!


