# Xray конфиги с роутингом для России 🇷🇺

## 📁 Файлы

| Файл | Ссылка | Описание |
|------|--------|----------|
| `routing.json` | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/routing.json) | Правила роутинга в формате для v2rayN |
| `routing_original.json` | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/routing_original.json) | Правила роутинга в нативном формате Xray |

---

## 🚀 Установка для Happ

| Роутинг | Диплинк | Raw JSON | Описание |
|---------|---------|----------|----------|
| **📶 Wi-Fi Routing** | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/wi_fi_routing.deeplink) | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/happ_wi_fi_routing.json) | РФ-сайты и IP напрямую, реклама заблокирована, остальное в прокси |
| **🔒 Whitelist Routing** | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/whitelist_routing.deeplink) | [Просмотр](https://raw.githubusercontent.com/AlwaysBusyStack/XrayRoutingConfigurations/refs/heads/master/happ_whitelist_routing.json) | Только приватные сети напрямую, всё остальное в прокси (строгий вайтлист) |

> **Чтобы установить роутинг:** открой ссылку «Просмотр» на устройстве с установленным [Happ](https://happ.su) — браузер подхватит `happ://` диплинк автоматически

### Отличия роутингов

| | Wi-Fi Routing | Whitelist Routing |
|-|--------------|------------------|
| `geosite:ru-available-only-inside` | ✅ Напрямую | ❌ Через прокси |
| `geoip:ru` | ✅ Напрямую | ❌ Через прокси |
| `geosite:private` + `geoip:private` | ✅ Напрямую | ✅ Напрямую |
| `geosite:category-ads-all` | 🚫 Блок | 🚫 Блок |
| Всё остальное | 🔵 Прокси | 🔵 Прокси |

---

## 🔧 GeoIP и GeoSite

Используются данные от [runetfreedom/russia-v2ray-rules-dat](https://github.com/runetfreedom/russia-v2ray-rules-dat):

| Файл | Ссылка |
|------|--------|
| `geoip.dat` | https://github.com/runetfreedom/russia-v2ray-rules-dat/releases/latest/download/geoip.dat |
| `geosite.dat` | https://github.com/runetfreedom/russia-v2ray-rules-dat/releases/latest/download/geosite.dat |

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
- ✅ **Российские сайты** — `geosite:ru-available-only-inside`
- ✅ **Российские IP** — `geoip:ru`

### 🔵 PROXY (через VPN)
- 🌐 **Всё остальное** — весь глобальный трафик через прокси (`0-65535`, `tcp+udp`)
