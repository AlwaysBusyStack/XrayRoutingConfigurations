# Xray конфиги с роутингом для России 🇷🇺

## 📁 Файлы конфигурации

| Файл | Клиент | Режим | Ссылка |
|------|--------|-------|--------|
| `v2rayn_wi_fi_routing.json` | V2RayN | Wi-Fi | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/v2rayn_wi_fi_routing.json) |
| `v2rayn_whitelist_routing.json` | V2RayN | Whitelist | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/v2rayn_whitelist_routing.json) |
| `xray_wi_fi_routing.json` | Xray (нативный) | Wi-Fi | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/xray_wi_fi_routing.json) |
| `xray_whitelist_routing.json` | Xray (нативный) | Whitelist | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/xray_whitelist_routing.json) |
| `nekobox_wi_fi_routing.json` | Nekobox Android | Wi-Fi | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/nekobox_wi_fi_routing.json) |
| `nekobox_whitelist_routing.json` | Nekobox Android | Whitelist | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/nekobox_whitelist_routing.json) |

---

### Отличия режимов роутинга

| | Wi-Fi Routing | Whitelist Routing |
|-|--------------|------------------|
| `geosite:ru-available-only-inside` | ✅ Напрямую | ❌ Через прокси |
| `geoip:ru` | ✅ Напрямую | ❌ Через прокси |
| `geosite:private` + `geoip:private` | ✅ Напрямую | ✅ Напрямую |
| `geosite:category-ads-all` | 🚫 Блок | 🚫 Блок |
| Всё остальное | 🔵 Прокси | 🔵 Прокси |

---

## 🚀 Установка для V2RayN

1. Скачать нужный файл (`v2rayn_wi_fi_routing.json` или `v2rayn_whitelist_routing.json`)
2. Открыть **V2RayN** → меню **Настройки** → **Настройки роутинга**
3. Нажать **Импортировать правила из файла** → выбрать скачанный файл
4. Нажать **ОК**, перезапустить V2RayN

> Не забудь обновить файлы геоданных в V2RayN: **Обновить** → **Обновить GeoIP и GeoSite**, либо вручную скачать `geoip.dat` и `geosite.dat` (ссылки ниже) и положить в папку с V2RayN.

---

## 📱 Установка для Nekobox (Android)

1. Скачать нужный файл (`nekobox_wi_fi_routing.json` или `nekobox_whitelist_routing.json`)
2. Открыть **Nekobox** → нижняя панель **Настройки** (⚙) → **Персонализация**
3. Нажать **Пользовательский конфиг** → вставить содержимое скачанного файла → **Сохранить**
4. Перезапустить туннель

> Для работы гео-правил Nekobox нужны файлы геоданных в формате `.db`. Скачай `geoip.db` и `geosite.db` (ссылки ниже) и укажи их в настройках: **Настройки** → **Маршрутизация** → **Путь к GeoIP / GeoSite**.

---

## 🔧 GeoIP и GeoSite

Используются данные от [runetfreedom/russia-v2ray-rules-dat](https://github.com/runetfreedom/russia-v2ray-rules-dat):

| Файл | Формат | Для | Ссылка |
|------|--------|-----|--------|
| `geoip.dat` | `.dat` | V2RayN, Xray | https://github.com/runetfreedom/russia-v2ray-rules-dat/releases/latest/download/geoip.dat |
| `geosite.dat` | `.dat` | V2RayN, Xray | https://github.com/runetfreedom/russia-v2ray-rules-dat/releases/latest/download/geosite.dat |
| `geoip.db` | `.db` | Nekobox | https://github.com/runetfreedom/russia-v2ray-rules-dat/releases/latest/download/geoip.db |
| `geosite.db` | `.db` | Nekobox | https://github.com/runetfreedom/russia-v2ray-rules-dat/releases/latest/download/geosite.db |

---

## 🌐 DNS

### Domestic (для российских доменов)
> **[Яндекс DNS](https://dns.yandex.ru/): `77.88.8.8`** — DoH: `https://77.88.8.8/dns-query`

### Remote (для всего остального)
> **[Cloudflare DNS](https://1.1.1.1/): `1.1.1.1`** — DoH: `https://1.1.1.1/dns-query`

---

## 🔀 Правила роутинга

### 🔴 BLOCK (блокировка)
- 🚫 **Реклама** — `geosite:category-ads-all`

### 🟢 DIRECT (прямое соединение)
- ✅ **BitTorrent** — торренты напрямую, без нагрузки на сервер
- ✅ **Приватные сети** — `geoip:private`
- ✅ **Приватные домены** — `geosite:private`
- ✅ **Российские сайты** — `geosite:ru-available-only-inside` *(только Wi-Fi режим)*
- ✅ **Российские IP** — `geoip:ru` *(только Wi-Fi режим)*

### 🔵 PROXY (через VPN)
- 🌐 **Всё остальное** — весь глобальный трафик через прокси (`0-65535`, `tcp+udp`)
