# Прошивки пульта МДКЗ

Лише готові прошивки, без коду. Екран пульта завантажує `manifest.json` і за ним — потрібні `.bin`.

```
manifest.json              ← поточна версія; на нього дивиться екран
CHANGELOG.md               ← зміни всіх версій
v<версія>/
  CHANGES.txt              ← що змінилось у цій версії
  mdkz_cab_display.bin     ← оновлення по повітрю і з карти пам'яті
  mdkz_cab_node.bin        ← вузол кабіни на ESP32-S3-DevKitC-1
  mdkz_cab_node_esp32.bin  ← вузол кабіни на ESP32 DevKit V1 (з 0.5.1)
  mdkz_relay_node.bin      ← обидва вузли реле
  kabel/                   ← прошивання кабелем, з адреси 0x0
    ekran-cab-display-0x0.bin
    vuzol-kabiny-cab-node-0x0.bin          ← ESP32-S3-DevKitC-1
    vuzol-kabiny-esp32-devkit-v1-0x0.bin   ← ESP32 DevKit V1
    vuzol-rele-relay-node-0x0.bin
```

**Оновлення з карти пам'яті:** скопіюйте файли `mdkz_*.bin` потрібної версії в папку `MDKZ` на карті microSD (FAT32), далі на екрані: Оновлення → «З карти пам'яті».

**Кабелем:** файли з `kabel/`, кожен з адреси 0x0 (esptool або https://espressif.github.io/esptool-js/).

Щоб повернутися до старішої версії, прошийте її кабелем: екран пропонує оновлення лише до новішої.

Код — у приватному репозиторії `AndreyVlasjuk/Mdkz`; файли сюди викладає `tools/publish_firmware.sh` або збірка GitHub Actions за тегом `v*`. Вручну тут нічого не змінюйте.
