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

## Аналізатор CAN і застосунок «CAN-монітор»

Окремий пристрій для шини J1939 вантажівки (ESP32-C3 SuperMini) і застосунок для Android до нього.

```
can-monitor/
  latest.json                    ← поточна версія; на нього дивиться застосунок
  can-monitor-<версія>.apk       ← застосунок; ставиться поверх попередньої версії
can-analyzer/
  latest.json                    ← поточна прошивка аналізатора; її бере застосунок
  can-analyzer-ota-<версія>.bin  ← оновлення по повітрю (застосунок або сторінка плати)
  kabel/can-analyzer-<версія>-esp32c3-supermini-0x0.bin  ← кабелем, з адреси 0x0
```

Оновлення: у застосунку ⚙ → «Перевірити оновлення» (застосунок) і «Оновити прошивку з інтернету» (плата).

Код — у приватному репозиторії `AndreyVlasjuk/Mdkz`; файли сюди викладає `tools/publish_firmware.sh` або збірка GitHub Actions за тегом `v*` (аналізатор і застосунок — `tools/publish_can_analyzer.sh`, `tools/publish_can_monitor.sh`, теги `can-analyzer-v*`, `can-monitor-v*`). Вручну тут нічого не змінюйте.
