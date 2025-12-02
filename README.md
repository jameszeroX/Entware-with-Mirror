# Entware-with-Mirror

В конце ноября 2025 года в России по непонятным причинам заблокировали репозиторий Entware для роутеров Keenetic/Netcraze, в результате чего на уже установленных системах перестали работать команды `opkg update`, `opkg upgrade` и установка пакетов командой `opkg install`
Это исправляется заменой в файле `/opt/etc/opkg.conf` ссылки репозитория на [зеркало](https://entware.net/mirrors.html) (обратите внимание на примечание на этой странице на счёт https-ссылок).

Пример, исправленного файла для роутеров на процессорах arm
```
src/gz entware http://mirrors.nju.edu.cn/entware/aarch64-k3.10
src/gz keendev http://mirrors.nju.edu.cn/entware/aarch64-k3.10/keenetic
dest root /
lists_dir ext /opt/var/opkg-lists
arch all 100
arch aarch64-3.10 150
arch aarch64-3.10_kn 200
```

Пример, исправленного файла для роутеров на процессорах mipsle
```
src/gz entware http://mirrors.nju.edu.cn/entware/mipselsf-k3.4
src/gz keendev http://mirrors.nju.edu.cn/entware/mipselsf-k3.4/keenetic
dest root /
lists_dir ext /opt/var/opkg-lists
arch all 100
arch mipsel-3.4 150
arch mipsel-3.4_kn 200
```

Однако, приведенный выше совет не решает проблему установки Entware с нуля, так как при этом загружаются пакеты из репозитория. Если репозиторий недоступен, то установка зависает. На [странице релизов](https://github.com/jameszeroX/Entware-with-Mirror/releases) выложил перепакованные дистрибутивы Entware с уже прописанным зеркалом, они позволят выполнить установку без ошибок в условиях недоступности официального репозитория.

### Справка
Для моделей 4G (KN-1212), Omni (KN-1410), Extra (KN-1710/1711/1713), Giga (KN-1010/1011), Ultra (KN-1810), Viva (KN-1910/1912/1913), Giant (KN-2610), Hero 4G (KN-2310/2311), Hopper (KN-3810) и Zyxel Keenetic II / III, Extra, Extra II, Giga II / III, Omni, Omni II, Viva, Ultra, Ultra II используйте для установки архив mipsel — [mipsel-installer.tar.gz](https://github.com/jameszeroX/Entware-with-Mirror/releases/latest/download/mipsel-installer.tar.gz)

Для моделей Ultra SE (KN-2510), Giga SE (KN-2410), DSL (KN-2010), Skipper DSL (KN-2112), Duo (KN-2110), Ultra SE (KN-2510),  Hopper DSL (KN-3610) и Zyxel Keenetic DSL, LTE, VOX используйте для установки архив mips — [mips-installer.tar.gz](https://github.com/jameszeroX/Entware-with-Mirror/releases/latest/download/mips-installer.tar.gz)

Для моделей Peak (KN-2710), Ultra (KN-1811), Giga (KN-1012), Hopper (KN-3811) и Hopper SE (KN-3812) используйте архив aarch64 — [aarch64-installer.tar.gz](https://github.com/jameszeroX/Entware-with-Mirror/releases/latest/download/aarch64-installer.tar.gz)

