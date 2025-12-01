# Entware-with-Mirror

В конце ноября 2025 года в России по непонятным причинам заблокировали репозиторий Entware для роутеров Keenetic/Netcraze, в результате чего на уже установленных системах перестали работать команды `opkg update`, `opkg upgrade` и установка пакетов командой `opkg install`
Это исправляется заменой в файле `opt/etc/opkg.conf` ссылки репозитория на [зеркало](https://entware.net/mirrors.html) (обратите внимание на примечание на этой странице на счёт https-ссылок).

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

Однако, приведенный выше совет не решает проблему установки Entware с нуля. При установке загружаются пакеты из репозитория, а если он недоступен, то установка зависает. На [странице релизов]( https://github.com/jameszeroX/Entware-with-Mirror/releases) выложил перепакованные дистрибутивы Entware с уже прописанным зеркалом, они позволят выполнить установку без ошибок в условиях недоступности официального репозитория.
