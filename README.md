<p align="center">
<img src="https://github.com/eminshakh/archlinux/blob/master/logo/logo.png" width="200">
</p>

## Установка
### Подключение к Wi-Fi:
1. ```iwctl```
2. ```device list```
3. ```station wlan0 scan```
4. ```station wlan0 get-networks```
5. ```station wlan0 connect "Network name"```
6. ```exit```

Вводим ```archinstall```

<p align="left">
<img src="https://github.com/eminshakh/archlinux/blob/master/logo/archinstall.png" width="800">
</p>

## Настройка
### Bluetooth:
``` bash 
sudo pacman -S bluez bluez-utils pulseaudio pulseaudio-bluetooth blueman pavucontrol
```
``` bash 
sudo systemctl start bluetooth
```
``` bash 
sudo systemctl enable bluetooth
```
### Git
``` bash 
sudo pacman -Syu git
```
### PARU (package install helper):
``` bash 
sudo pacman -Syu --needed base-devel
```
``` bash 
git clone https://aur.archlinux.org/paru.git && cd paru && makepkg -si
```
### Python
``` bash 
sudo paru -S python python-pipe
```
### Golang:
``` bash 
sudo pacman -S go
```
### Goland:
``` bash 
paru -S goland jre-openjdk jdk-openjdk
```
### Slack
``` bash 
paru -S slack-desktop
```
### Zoom
``` bash 
paru -S zoom
```
### Telegram
``` bash 
paru -S telegram-desktop
```
### Браузер Chromium
``` bash 
paru -S chromium
```
### Docker:
``` bash 
paru -S docker
```
``` bash 
systemctl start docker
```
``` bash 
systemctl enable docker
```
``` bash 
sudo gpasswd -a $USER docker
```
### KDE Dock как в Mac-OS:
``` bash 
paru -S latte-dock
```
### Reflector (получение и сортировка по скорости списка зеркал Pacman)
``` bash 
paru -S reflector
```
``` bash 
sudo vim /etc/xdg/reflector/reflector.conf
```
изменить в файле reflector.conf:
* --latest 20
* --sort rate
``` bash 
sudo systemctl start reflector
```
### Ananicy (контроль приоритета задач)
``` bash 
paru -S ananicy
```
``` bash 
sudo systemctl enable --now ananicy
```
### Fish (оболочка терминала):
``` bash 
paru -S fish
```
``` bash 
chsh
```
Ввести: /bin/fish
``` bash 
reboot
```
``` bash 
sudo vim /etc/pacman.conf
```
раскомментировать строку //Color
``` bash 
fish_config
```
Выбрать в браузере тему fish
### Выключить писк при выключении:
``` bash 
sudo vim /etc/modprobe.d/nobeep.conf
```
прописать строку:
`blacklist    pcspkr`
### Включение OpenGL
``` bash 
sudo pacman -S xf86-video-ati
```
``` bash 
sudo su
```
``` bash 
echo "MESA_GL_VERSION_OVERRIDE=4.5" >> /etc/environment
```
``` bash 
echo "MESA_GLSL_VERSION_OVERRIDE=450" >> /etc/environment
```
### Включаем службу Trim файловой системы (для SSD)
``` bash 
sudo systemctl enable fstrim.timer 
```
``` bash 
sudo fstrim -va 
```
### Оптимизации SSD
``` bash 
sudo vim /etc/fstab 
```
добавить
`rw,relatime,ssd,ssd_spread,space_cache=v2,max_inline=256,commit=600,nodatacow` до `.subvol=/`
### Haveged (демон, что следит за энтропией системы. Ускорения запуска системы)
``` bash 
sudo pacman -S haveged
```
``` bash 
sudo systemctl enable haveged
```
### Отключение NetworkManager-wait-online
NetworkManager задерживает загрузку системы примерно на ~4 секунды.
``` bash 
sudo systemctl mask NetworkManager-wait-online.service
```
### Auto-Cpufreq (автоматический оптимизатор скорости процессора)
``` bash 
git clone https://aur.archlinux.org/auto-cpufreq-git.git && cd auto-cpufreq-git && makepkg -sric
```
``` bash 
systemctl enable auto-cpufreq
```
``` bash 
systemctl start auto-cpufreq
```
### Ноутбук Lenovo ThinkBook G2 ARE не выходит из сна на Linux. Решение:
``` bash 
sudo vim /etc/default/grub
```
Изменить строку на:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=off"
``` bash 
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
``` bash 
reboot
```
### Dry (менеджер для Docker)
``` bash 
curl -sSf https://moncho.github.io/dry/dryup.sh | sudo sh
```
``` bash 
sudo chmod 755 /usr/local/bin/dry
```
### 3mux (терминальный мультиплексор)
``` bash 
paru -S 3mux
```
### mkcert (на localhost для часто употребляемых тестовых имён выписать валидный сертификат)
``` bash 
paru -S mkcert
```
### man-db (мануал. man "команда")
``` bash 
paru -S man-db
```
### NTFS драйвер
``` bash 
paru -S ntfs-3g
```
### Очистка системы
``` bash 
paru -S stacer
```
### Neofetch (выводит в терминал информацию о системе)
``` bash 
paru -S neofetch
```
### Миниатюры для видео в Dolphin
``` bash 
paru -S ffmpegthumbs
```
### Архиваторы
``` bash 
paru -S ark, p7zip, unrar
```
### Менеджеры дисков
``` bash 
paru -S gparted
```
### Торрент клиент
``` bash 
paru -S qbittorrent
```
### Резервное копирование
``` bash 
paru -S timeshift
```
### Шрифты
``` bash 
paru -S noto-fonts noto-fonts-cjk noto-fonts-emoji noto-fonts-extra ttf-nerd-fonts-symbols
```
### Просмотр изображений
``` bash 
paru -S gThumb
```
### Скриншоты
``` bash 
paru -S flameshot
```
### Видеоплеер
``` bash 
paru -S haruna
```
### Информация о медиафайле
``` bash 
paru -S mediainfo-gui
```
### Офис
``` bash 
paru -S libreoffice-still
```
### Kate (аналог блокнота)
``` bash 
paru -S kate
```
### Сетевые клиенты и серверы (ftp, ping, rcp, rlogin, rsh, talk, telnet и tftp)
``` bash 
paru -S inetutils
```
### kubectl (управления кластерами Kubernetes)
``` bash 
paru -S kubectl
```
### Kitty (терминал)
``` bash 
paru -S kitty
```
### Btrfs-progs
``` bash 
paru -S btrfs-progs
```
### lsof (кто использует файл или порт)
``` bash 
paru -S lsof
```
