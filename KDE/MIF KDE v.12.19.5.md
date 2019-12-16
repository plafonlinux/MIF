
#
#### <center>*Для начала советую ознакомится со всеми проектами от  @plafonlinux:*

### <center> [Полный список ссылок на наши проекты](https://vk.com/plafonlinux?w=wall-151303502_5816)

### <center> [Полноценный стрим по на стройке Manjaro KDE](https://www.youtube.com/watch?v=FlSjU4s1uKo)

###### По всем вопросам, можете обращаться в наш [Чат в Телеграме](https://t.me/plafonlinuxchat), а если нашли замечания или нестыковки в данном файле, пишите мне в [личку в ВК](https://vk.com/bvffer) или напрямую в Телеграме.

###### Для корректного отображения файла, необходимо скачать модуль [gedit-markdown](https://github.com/jpfleury/gedit-markdown) и включить его в Правка - Параметры - Модули - Markdown Preview:

``` 
mkdir -p ~/.local/share/gedit/plugins/
cd ~/.local/share/gedit/plugins/
git clone https://github.com/aliva/gedit-markdownpreview.git markdownpreview
```
#
# <center> M.I.F. KDE - Manjaro Install File KDE v.12.19  


- ## Как правильно разметить диск для твоего Линукса?

####Вариант 1: Для тех у кого мало места или для самых экономных

```
boot/efi                                [FAT32] = 300 Мб
                                        [btrfs/EXT4] = 30730 Мб = 30 Гб
/home                                   [EXT4]  = все оставшееся место
```

####Вариант 2: Мои варианты разметки, который некоторые критикует, за не бережность к свободному месту, но я уже много лет примерно так и размечаю систему и всем остаюсь доволен ... На ваш выбор вообщем ...

### - На примере SSD 120 Гб = 112640 Мб

```
boot/efi                                [FAT32] = 300 Мб
/                                       [btrfs] = 30730 Мб = 30 Гб
/home                                   [EXT4]  = 76800 Мб = 75 Гб
неразмеченная область                   [----]  = 4810  Мб  = 4 Гб
```

### - На примере SSD 120 Гб + HDD на 500 Гб (так у меня на ноутбуке)

- SSD KingDian на 120гб (EFI, /, SWAP зашифрованный раздел и 5гб неразмеченной области)
- Отдельный жёсткий диск на 500гб (/home)

```
boot/efi                                [FAT32] = 300 Мб
/                                       [btrfs] = 100 гб
*Зашифрованный раздел                   [LUKS]  = 2 Гб                   // для паролей и личных данных 
/home -                                 [EXT4]  = 500 Гб                // для надёжного хранения данных
```

### - На примере SSD 250Гб = 245760 Мб

```
boot/efi                                [FAT32] = 300    Мб
/ + /timeshift                          [btrfs] = 51200  Мб = 50  Гб
/home                                   [EXT4]  = 174080 Мб = 160 Гб
/swap                                   [SWAP]  = 8192   Мб = 8   Гб       // при наличие 8+ Гб ОЗУ можно вообще не делать 
неразмеченная область (только для SSD)  [----]  = 11988  Мб               // делаю, чтобы не забивать окончательно SSD и плюс свободные сектора под битые блоки
```

### - На примере SSD 500Гб = 501760 Мб

```
boot/efi                                [FAT32] = 512   Mb               // Можно смело делать 300 Мб
/                                       [btrfs] = 51200 Мб = 50 Гб
/timeshift                              [btrfs] = 51200 Мб = 50 Гб
/swap                                   [SWAP]  = 16384 Мб = 16 Гб      // При наличие 8+ Гб ОЗУ можно вообще не делать, лично я делаю SWAP для DaVinci Resolve
/home                                   [EXT4]  = 358400 Мб = 350Гб
неразмеченная область (только для SSD)  [----]  = 24064 Мб               // делаю, чтобы не забивать окончательно SSD и плюс свободные сектора под битые блоки
```

#

МОЯ АКТУАЛЬНАЯ РАЗМЕТКА НА ОСНОВНОМ ПК

#

### - SAMSUNG SSD 500Гб = 501760 Мб

```
boot/efi                                [FAT32] = 300   Mb                          // Можно смело делать 300 Мб
/                                       [btrfs] = 51200 Мб = 50 Гб                 // Корень системы, переустанавливаю сюда новую систему, когда вдруг невозможно откатиться (крайне редко)
/timeshift                              [btrfs] = 51200 Мб = 50 Гб                // Здесь хранятся полноценные снимки системы в BTRFS и RSYNC 
/swap                                   [SWAP]  = 16384 Мб = 16 Гб               // При наличие 8+ Гб ОЗУ можно вообще не делать, лично я делаю SWAP для DaVinci Resolve
/home                                   [LUKS][EXT4]  = 358400 Мб = 350 Гб      // Зашифрованный домашний раздел для файлов, видео, скриншотов и всякого хлама в хомяке
/secret                                 [LUKS][EXT4]  = 3584 Mб = 3,5 Гб       // Зашифрованный раздел для хранение паролей (в текстовом формате) и некоторых личных данных  
неразмеченная область (только для SSD)  [----]  = 24276 Мб                    // делаю, чтобы не забивать окончательно SSD и плюс свободные сектора под битые блоки
```

#
- #### Самое первое установим нужные нам утилиты: ```sudo pacman -S yay neofetch inxi```
# 


## 01. НАСТРОЙКА ВИДЕОКАРТ ОТ NVIDIA - [ТЕСТ НА ТИРИНГ](https://bit.ly/34MoP8R)

#### - Настройка [Nvidia Settings](https://bit.ly/2rEpDy3) + [GreenWithEnvy](gitlab.com/leinardi/gwe)

Для начала приводим настройки вашего Nvidia-Settings как [здесь](https://bit.ly/2rEpDy3) 

И после того, как произвели все настройки, сохраняем их по этому пути (от суперпользователя): 

 ``` sudo nvidia-settings ``` и сохраняем настройки ``` /etc/X11/mhwd.d/nvidia.conf ```

- Включаем опцию разгона для вашей видеокарты (на примере моей 1050Ti)

```
sudo mkdir /etc/X11/xorg.conf.d/
sudo gedit /etc/X11/xorg.conf.d/20-nvidia.conf
```
далее нужно добавить в него это:

```
Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce GTX 1050Ti"
#если у вас уже есть настройки в файле, достаточно добавить два пункта ниже.
Option "RegistryDwords" "PerfLevelSrc=0x2222"
Option "TripleBuffer" "True"
Option "Coolbits" "28"
EndSection
Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "Stereo" "0"
Option "nvidiaXineramaInfoOrder" "DFP-0"
#если у вас уже есть настройки в файле, достаточно добавить пункт ниже.
Option "metamodes" "nvidia-auto-select +0+0 { ForceFullCompositionPipeline = On }"
Option "SLI" "Off"
Option "MultiGPU" "Off"
Option "BaseMosaic" "off"
SubSection "Display"
Depth 24
EndSubSection
EndSection
```
Сохраняемся и перезапускаем ПК

- Далее устанавливаем утилиту [GWE - GreenWithEnvy](https://bit.ly/2R60W87) (утилита для разгона видеокарты и управлением охлаждения)
```
sudo pacman -S gwe

```
#

## 02. НАСТРОЙКА ВИДЕОКАРТ ОТ AMD

- Включаем видоекарты AMD: ``` DRI_PRIME=1 glxinfo | grep -i opengl  ```
- Включаем встроенную графику от Intel: ```  DRI_PRIME=0 glxinfo | grep -i opengl  ```

#### AMD GPU OVERCLOCKING / UNDERVOLTING (RX400\500+VEGA 56\64)

- Нужно обязательно добавить в загрузку ядра флаг разрешающий управлять питанием карты:
зайдите в файл конфигурации grub:

В терминале выполняем: ``` sudo gedit /etc/default/grub   ```

и меняем строку: ``` GRUB_CMDLINE_LINUX_DEFAULT=""    ``` на: ``` GRUB_CMDLINE_LINUX_DEFAULT="amdgpu.ppfeaturemask=0xffffffff"    ```

- если строка не пуста, добавьте значения через пробел к остальным далее обновляем GRUB:  

 ``` sudo grub-mkconfig -o /boot/grub/grub.cfg    ``` 

- Теперь можно делать разгон и управлять питанием через утилиты: corectrl, radeon-profile

#### УТИЛИТА RADEON-PROFILE ДЛЯ АВТОМАТИЧЕСКОГО УПРАВЛЕНИЯ ВЕНТИЛЯТОРАМИ И РАЗГОНОМ ВИДЕОКАРТ AMD'

 ``` yay radeon-profile-git  ``` 

## 03. ДОБАВЛЯЕМ В MANJARO ВСЕ НЕОБХОДИМЫЕ ШРИФТЫ: [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)

 ``` yay ttf-win10 ``` 
 ``` yay ttf-windows ``` 
 ``` yay nerd-fonts-complete ``` 
 ``` yay nerd-fonts-dejavu-complete ``` 
 ``` yay ttf-bitstream-vera ``` 
 ``` yay ttf-droid ``` 
 ``` yay ttf-inconsolata ``` 
 ``` yay ttf-indic-otf ``` 
 ``` yay ttf-liberation ``` 

#

## 04. УБИРАЕМ СФЕТОФОР С ТРЕЯ

- Установка проста но к сожалению очень продолжительная

 ``` yay -S hardcode-tray-git sni-qt-patched-git lib32-sni-qt-patched-git ``` 

- После установки вы може заменить светофорные иконки командой:

###### Где —theme Tela  или KDE_Classic,  —size 16 или 22 или 24 

###### argument --theme: invalid choice: 'Papirus-Dark' (choose from 'Adwaita', 'Breeze_Snow', 'HighContrast', 'KDE_Classic', 'Oxygen_Black', 'Oxygen_Blue', 'Oxygen_White', 'Oxygen_Yellow', 'Oxygen_Zion', 'Tela', 'Tela-dark', 'breath', 'breeze', 'breeze-dark', 'breeze_cursors', 'default', 'gnome', 'hicolor', 'oxygen'

 ``` sudo -E hardcode-tray --conversion-tool RSVGConvert --size 22 --theme Tela
 ``` 

- И перезагружаем ПК

Источник: https://archblog.pro/?p=659

#

## 05. ОПТИМИЗАЦИЯ СИСТЕМЫ И SSD

#### - УМЕНЬШЕНИЕ ИСПОЛЬЗОВАНИЯ ФАЙЛА ПОДКАЧКИ (использовать если у вас памяти более 3Гб RAM):

 ``` echo -e "vm.swappiness=10" | sudo tee -a /etc/sysctl.conf ``` 

#### - Параметр ниже использовать только если у вас надежный SSD и 8Гб+ Памяти

 ``` echo -e "vm.vfs_cache_pressure=1000" | sudo tee -a /etc/sysctl.conf ``` 

#### - УСКОРЕНИЕ MANJARO ЕСЛИ У ВАС ССД ДИСК + ПАМЯТЬ 8Гб+  [НЕ ВСЕМ ПОДОЙДЕТ]

 ``` vm.dirty_background_ratio  ``` - размер оперативной памяти для размещения подготовленных для записи страниц кэша.
 ``` vm.dirty_ratio  ``` - размер оперативной памяти для размещения общего кэша записи.
Все эти параметры записываются в файл  ``` sudo gedit /etc/sysctl.conf ``` 
Узнать текущие значения этих параметров можно командой  ``` sysctl -a | grep dirty. dirty ``` 
Пример 1. Увеличение размера кэша записи (ускорение работы системы):
 ``` vm.dirty_background_ratio = 50 ``` 
 ``` vm.dirty_ratio = 80 ``` 
Пример 2. Уменьшение размера кэша записи:
 ``` vm.dirty_background_ratio = 5 ``` 
 ``` vm.dirty_ratio = 10 ``` 

 ``` echo -e "vm.dirty_background_ratio = 50" | sudo tee -a /etc/sysctl.conf ``` 

 ``` echo -e "vm.dirty_ratio = 80" | sudo tee -a /etc/sysctl.conf ``` 

#### - TMP ПАПКУ В ОПЕРАТИВНУЮ ПАМЯТЬ

 ``` echo 'tmpfs /tmp tmpfs noatime,nodiratime,mode=1777,size=50% 0 0' | sudo tee -a /etc/fstab ``` 

- Здесь size=50% устанавливает максимальный объём диска в половину всей физической памяти (это также и значение по умолчанию). Изменения вступят в силу после перезагрузки.

#### - ДЛЯ РАБОТЫ С SSD НУЖНО ВЫСТАВИТЬ ФЛАГИ В /ETC/FSTAB':  "sudo gedit /etc/fstab"

- Примечание:

- TRIM не включается по умолчанию при использовании шифрования блочных устройств на SSD; для дополнительной информации смотрите Dm-crypt/TRIM support for SSD.
- Нет необходимости использовать флаг discard, если вы периодически запускаете fstrim (пункт ниже).
- Использование флага discard для корневого раздела с файловой системой ext3 приведёт к тому, что он будет смонтирован в режиме только-чтение.

 ``` ssd,discard (Defaults - этот убираем) ```  - ДЛЯ BTRFS.

ДЛЯ EXT4 РЕКОМЕНДУЮ ИСПОЛЬЗОВАТЬ LAZYTIME!

 ``` / ext4 lazytime,errors=remount-ro 0 1 ``` 

 ``` /home ext4 lazytime 0 2 ``` 

#### - ВКЛЮЧЕНИЕ TRIM ПО РАСПИСАНИЮ'

- Проверьте, если ваш SSD поддерживает функцию TRIM:  ``` hdparm -I /dev/sda | grep TRIM ``` 

- TRIM позволяет поддерживать SSD-накопитель в форме, вовремя помечая неиспользуемые блоки. Можно прописать в планировщике еженедельную команду TRIM

 ``` sudo gedit /etc/cron.weekly/fstrim ``` 

и добавляем это:

``` 
#!/bin/sh
# trim all mounted file systems which support it
/sbin/fstrim --all || true
exit 0 
```
 
### - Оптимизация питания в ноутбуке и отпечаток пальца

#### - TLP - LINUX ADVANCED POWER MANAGEMENT (Альтернативное управления питанием в Linux)

 ``` yay tlp  ```                // В Manjaro KDE идет из коробки

#### - АВТОМАТИЧЕСКОЕ ОТКЛЮЧЕНИЕ TOUCHPAD ЕСЛИ ПОДКЛЮЧЕНА МЫШЬ К НОУТБУКУ

 ``` yay touchpad-indicator-git ``` 

#### - ЗАПУСК РАБОТЫ ОТПЕЧАТКА ПАЛЬЦА НА НОУТБУКАХ HP

 ``` yay fingerprint-gui ``` 

#
###### Источник: [BZU для Ubuntu](https://bit.ly/2DySTsD)
# 

## 06. ОФОРМЛЕНИЕ СИСТЕМЫ | [ПАК КРАСИВЫХ ОБОИН ДЛЯ ДЕСКТОПА](https://bit.ly/2DJi77P)

#### - МОИ ТЕМЫ И ЦВЕТОВЫЕ СХЕМЫ ДЛЯ KDE | [ПАК ОФОРМЛЕНИЯ от @plafonlinux](https://vk.com/plafonlinux?w=wall-151303502_5823) |

 ``` Тема для окон:```     [BreezeEnhanced](yay breeze-enhanced-git) 

 ``` Тема для Plasma:```   [Layan Dark](https://store.kde.org/p/1325243) 

 ``` Тема для GTK2/3: ```  [Dark-Olympic](https://store.kde.org/p/1302313/) 

 ``` Icons: ```            [Tela-dark](https://store.kde.org/p/1279924/) 

 ``` Курсор:  ```                              ``` Breeze, светлый вариант ``` 

 ``` DPI для FullHD:  ```                      ``` 101 ``` 

#### - Один из лучших доков [Latte Dock](https://vk.com/plafonlinux?w=wall-151303502_6004) (если не лучший) для Manjaro KDE

 ``` sudo pacman -S latte-dock  ``` 

- [Все мои настройки для Latte Dock](https://vk.com/plafonlinux?w=wall-151303502_6004)

#

## 07. НАСТРАИВАЕМ MANJARO LINUX ДЛЯ ИГР

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
######Источник: [Проект PortWine](http://portwine-linux.ru/portwine-faq/)
#

## 08. [НАБОР НЕОБХОДИМОГО СОФТА](https://docs.google.com/document/d/1Aul7Ds7wuaWA6LtvQB8qGTFKy0aMgTORN-1Yvz-hYCo/edit#heading=h.ky2zvj1r8b3q)

                                            ВЕБ СЕРФИНГ | МЕССЕНДЖЕРЫ | ТОРРЕНТЫ 

 ``` sudo pacman -S firefox  ```                      | Мой основной браузер, принятый стандарт в мире Linux

 ``` yay google-chrome  ```                           | Google Chrome коммерческий продукт от компании Google

 ``` sudo pacman -S chromium ```                      | Некоммерческий форк Google Chrome (в плане использования один в один)

 ``` sudo pacman -S telegram-desktop ```              | Телегам, мессенджер от нашего земляка, для Desktop

 ``` yay whatsapp-nativefier  ```                     | Неофициальный WhatsApp-мессенджер для Desktop, но работает все отлично

 ``` sudo pacman -S  qbittorrent ```                  | Самый крутой кроссплатформенный торрент-клиент, которым я когда либо пользовался


                                            ТЕКСТ | ДОКУМЕНТЫ | КОДИНГ

 ``` sudo pacman -S gedit  ```                        | Мой основной текстовый редактор от Gnome 3

 ``` sudo pacman -S kate   ```                        | Альтернативный крутой текстовый редактор

 ``` sudo pacman -S onlyoffice-desktopeditors ```     | Лучшая замена Word, Exel, Power Point от наших земляков


                                            ВИДЕО | АУДИО | МОНТАЖ

 ``` sudo pacman -S shotcut     ```                   | Один из самых крутых open source видео-редакторов с удобным таймлайном, кучей эффектов и ключевыми кадрами

 ``` sudo pacman -S blender  ```                      | 3D и видео монтаж\обработка, а также игровой движок

 ``` sudo pacman -S kdenlive    ```                   | Достаточно популярный видео-редактор 

 ``` sudo pacman -S audacity   ```                    | Мощный аудиоредактор для обработки вашего звука

 ``` sudo pacman -S ffmpeg   ```                      | Мощный консольный видео-конвертер

 ``` sudo pacman -S winff    ```                      | Графическая оболочкой (GUI) для мощного консольного видео-конвертора FFMPEG. 

                                            DAVICNI RESOLVE STUDIO

- Регистрируемся и [скачиваем архив с официального сайта](https://www.blackmagicdesign.com/ru/products/davinciresolve/) в папку Загрузки

 ``` yay davinci-resolve    ```                       | Смело можно назвать аналогом любого профессионального видео-редактора.       

 - [Подробное видео по установке DaVinci Resolve в Manjaro Linux](https://www.youtube.com/watch?v=xMxLRVKLiq0&t=13s)
                        
### - На Линуксе есть ограничения в бесплатной версии, как их обойти и какие костыли использовать:

- [СКАЧАТЬ СКРИПТ ДЛЯ АВТОМАТИЧЕСКОЙ КОНВЕРТАЦИИ В PRORES](https://drive.google.com/open?id=1MoOL_3FWb0hy0qEpc7ZopHaEHEhAda3D)
- [В КАКОМ ФОРМАТЕ ЗАПИСЫВАТЬ РАБОЧИЙ СТОЛ ДЛЯ DAVICNI RESOLVE](https://bit.ly/2rEH4hZ)

                                            СТРИМЫ | YOUTUBE | ДОНАТЫ

 ``` sudo pacman -S obs-studio   ```                  | Одна из самый крутых програм по бродкастингу, если забыть про StreamLabs OBS, которого до сих-пор нет под Линукс. Поддерживает Nvidia Nvenc.

 ``` sudo pacman -S simplescreenrecorder   ```        | Более простая программа для захвата экрана или отдельного окна, без поддержки Nvidia Nvenc.

 ``` sudo pacman -S peek   ```                        | Написан на Vala Language. Умеет записывать отдельные области экрана, а так-же создавать анимированные GIF-изображения.


                                              OBS + LINUX BROWSER PLUGIN 

<center>[МОИ НАСТРОЙКИ OBS](https://bit.ly/2PgKVK2)</center>

 ``` sudo pacman -S obs-studio ``` | Устанавливаем OBS Studio для Manjaro Linux

 ``` yay obs-linuxbrowser-bin ```  | Устанавливаем плагин браузера для OBS Studio


                                            ИЗОБРАЖЕНИЯ | ФОТОГРАФИИ | СКРИНШОТЫ
               
 ``` sudo pacman -S gthumb   ```                      | Самая крутая утилита для просмотра изображений и их каталогизации

 ``` sudo pacman -S krita    ```                      | Достойная бесплатная альтернатива Photoshop, умеет читать .psd, поддерживает графические планшеты для художников

 ``` sudo pacman -S darktable   ```                   | Редактирование и обработка фотографий, поддержка Raw

 ``` sudo pacman -S spectacle  ```                    | Мощный инструмент для снятия скриншотов и их загрузки сразу в хостинг картинок
                       






#
#

#####<center> ``` КОНЕЦ ФАЙЛА M.I.F. ``` </center>

#
#
  
#### <center>*Для начала советую ознакомится со всеми проектами от  @plafonlinux:*

### <center> [Полный список ссылок на наши проекты](https://vk.com/plafonlinux?w=wall-151303502_5816)

### <center> [Полноценный стрим по на стройке Manjaro KDE](https://www.youtube.com/watch?v=FlSjU4s1uKo)

###### По всем вопросам, можете обращаться в наш [Чат в Телеграме](https://t.me/plafonlinuxchat), а если нашли замечания или нестыковки в данном файле, пишите мне в [личку в ВК](https://vk.com/bvffer) или напрямую в Телеграме.

###### Для корректоного отображения файла, необходимо скачать модуль [gedit-markdown](https://github.com/jpfleury/gedit-markdown) и включить его в Правка - Параметры - Модули - Markdown Preview:

``` 
mkdir -p ~/.local/share/gedit/plugins/
cd ~/.local/share/gedit/plugins/
git clone https://github.com/aliva/gedit-markdownpreview.git markdownpreview
```

#
# 
                                                КАК ВОCСТАНОВИТЬ СИСТЕМУ ЧЕРЕЗ TIMESHIFT

# 

### Опции восстановления:

- Разные списки:

 ``` --list[-snapshots]  ```         | Список точек восстановления

 ``` --list-devices    ```           | Список устройств

- Бэкап:

 ``` --check   ```                   | Создать точку восстановления (если необходимо)

 ``` --create  ```                   | Создать точку восстановления (даже если это не нужно)

 ``` --comments <string>  ```        | Создать комментарий для точки восстановления


- Восстановления системы:

 ``` --restore    ```                | Восстановить систему и выбрать доступную точку из списка далее

 ``` --clone      ```                | Клонировать актуальную систему

 ``` --snapshot <name>   ```         | Если вы точно знаете, какую точку хотите восстановить, укажите ее в данной команде

 ``` --target[-device] <device>  ``` | Выберите устройство

 ``` --grub[-device] <device>   ```  | Укажите устройство на которое должен быть установлен GRUB

 ``` --skip-grub             ```     | Восстановить систему без переустановки GRUB

- Ручное удаление точек восстановления:

 ``` --delete      ```               | Удалить точку восстановления

 ``` --delete-all     ```            | Удалить все точки восстановления

- Глобальные настройки Timeshift:

 ``` --snapshot-device <device>  ``` | Specify backup device (default: config)

 ``` --yes   ```                     | Ответить "ДА" на все последующие вопросы скрипта

 ``` --btrfs    ```                  | Перейти в BTRFS mode (default: config)

 ``` --rsync  ```                    | Перейти в RSYNC mode (default: config)

 ``` --debug   ```                   | Показать весь список ошибок

 ``` --verbose  ```                  | Show rsync output (default)

 ``` --quiet      ```                | Hide rsync output

 ``` --scripted    ```               | Run in non-interactive mode

 ``` --help    ```                   | Show all options

### Пример команд в Timeshift:

 ``` timeshift --list ``` 

 ``` timeshift --list --snapshot-device /dev/sda1 ``` 

 ``` timeshift --create --comments "after update" --tags D ``` 

 ``` timeshift --restore  ``` 

 ``` timeshift --restore --snapshot '2014-10-12_16-29-08' --target /dev/sda1 ``` 

 ``` timeshift --delete  --snapshot '2014-10-12_16-29-08' ``` 

 ``` timeshift --delete-all  ``` 


                                                РАЗНЫЕ ОШИБКИ И ПРОБЛЕМЫ

# 

#### - ОШИБКА "SPARSE" ПРИ ЗАГРУЗКЕ СИСТЕМЫ В BTRFS НА MANJARO LINUX

- Если после установки системы в BTRFS, вам выдает ошибку "sparce что-то там", лечим так": 

 ``` sudo gedit /etc/default/grub ``` 

Меняем  ``` GRUB_SAVEDEFAULT="true" ```  на  ``` GRUB_SAVEDEFAULT="false" ``` 

- Перезагружаемся, ошибка должа исчезнуть и система загрузится нормально

#

- Если-же ошибка после перезагрузки не ушла, то обновляем Grub:

 ``` sudo grub-mkconfig -o /boot/grub/grub.cfg ``` 

 ``` alias update-grub="sudo grub-mkconfig -o /boot/grub/grub.cfg" ``` 

скопировать в /home/ИМЯ_ПОЛЬЗОВАТЕЛЯ/.bashrc

#
#

#### - Процесс kworker грузит процессор: [Пример на моем ноутбуке](https://bit.ly/2ODlLWY)

Открываем ``` sudo gedit /etc/default/grub ```  и добавляем в  ``` GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" ``` 

параметр ``` pcie_aspm=off ``` 

- Должно получится вот так (если есть другие параметры ядра добавляем в конец строки через пробел pcie_aspm=off):

 ``` GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off" ``` 

 ``` sudo grub-mkconfig -o /boot/grub/grub.cfg ``` 


#
#

####<center>  ``` ПРОЕКТ @PLAFONLINUX (2017-2020)  ```  </center>

#
#













