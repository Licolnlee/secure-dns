[English](https://github.com/francis-zhao/secure-dns/) | [简体中文](https://github.com/francis-zhao/secure-dns/blob/master/README.cmn-CN.md) | 繁體中文

# 安全 DNS

## 簡介

此倉庫是 [paulmillr/encrypted-dns](https://github.com/paulmillr/encrypted-dns) 的一個分支，主要存放了用於蘋果設備的 [DNS over HTTPS (DoH)](https://zh.wikipedia.org/wiki/DNS_over_HTTPS) 和 [DNS over TLS (DoT)](https://zh.wikipedia.org/wiki/DNS_over_TLS) 設定描述檔。

相比原倉庫，此分支的所有描述檔均重新分配了獨立的 UUID，且將同一供應商的所有 DoH 和 DoT 設定集成在一個文件中，可以更方便地在系統設定中隨時切換和管理。

### 注意事項

根據 Google [這篇文章](https://security.googleblog.com/2022/07/dns-over-http3-in-android.html)的介紹，在支持 HTTP/3 的設備上，DNS over HTTP/3 (DoH3) 比 DoT 的性能更優。

從 iOS 和 iPadOS 15.5 開始，為了簡化咖啡館、飯店、機場等公共場所 Wi-Fi 的身份認證，蘋果將這些 Wi-Fi 的[強制網路門戶](https://zh.wikipedia.org/zh-tw/%E5%BC%BA%E5%88%B6%E9%97%A8%E6%88%B7)加入到了加密 DNS 豁免清單中。這是個好消息，但還有一些其他問題我們無法修復，只有等蘋果來解決：

- 無法啟用加密 DNS：[Little Snitch & Lulu](https://github.com/paulmillr/encrypted-dns/issues/13)、[VPN](https://github.com/paulmillr/encrypted-dns/issues/18)
- 部分流量繞過加密 DNS：[終端機和 App Store](https://github.com/paulmillr/encrypted-dns/issues/22)、[Chrome 瀏覽器](https://github.com/paulmillr/encrypted-dns/issues/19)

如果你需要更進一步的隱私保護，請查看[使用 Tor 網路的加密 DNS](https://github.com/alecmuffett/dohot)。

## 供應商

「`審查=是`」意味著描述檔不會發送某些主機「`主機名=IP`」關係的真實訊息。

| 名稱                                             | 區域  | 審查 | 備註                                                             | 安裝連結                            |
| ------------------------------------------------ | ----- | ---- | ---------------------------------------------------------------- | ----------------------------------- |
| [360 安全 DNS][360-security-dns]                 | 🇨🇳    | 是   | 由 360 數字安全集團運營                                          | [DoH/DoT][360-security-dns-profile] |
| [AdGuard DNS 默認][adguard-dns-default]          | 🇷🇺    | 是   | 由 AdGuard 運營，攔截廣告、跟蹤器和釣魚網站                      | [DoH/DoT][adguard-dns-profile]      |
| [AdGuard DNS 家庭保護][adguard-dns-family]       | 🇷🇺    | 是   | 由 AdGuard 運營，除默認規則外，額外攔截惡意軟體和成人內容        | [DoH/DoT][adguard-dns-profile]      |
| [AdGuard DNS 無過濾][adguard-dns-unfiltered]     | 🇷🇺    | 否   | 由 AdGuard 運營，無攔截                                          | [DoH/DoT][adguard-dns-profile]      |
| [Alekberg 加密 DNS][alekberg-dns]                | 🇳🇱    | 否   | 由個人提供                                                       | [DoH][alekberg-dns-profile]         |
| [阿里雲公共 DNS][aliyun-dns]                     | 🇨🇳    | 否   | 由阿里雲計算運營                                                 | [DoH/DoT][aliyun-dns-profile]       |
| [BlahDNS CDN 過濾][blahdns]                      | 🇺🇸    | 是   | 由個人提供，攔截廣告、跟蹤器和惡意軟體                           | [DoH/DoT][blahdns-profile]          |
| [BlahDNS CDN 無過濾][blahdns]                    | 🇺🇸    | 否   | 由個人提供，無過濾                                               | [DoH/DoT][blahdns-profile]          |
| [BlahDNS 芬蘭][blahdns]                          | 🇫🇮    | 是   | 由個人提供，攔截廣告、跟蹤器和惡意軟體                           | [DoH/DoT][blahdns-profile]          |
| [BlahDNS 德國][blahdns]                          | 🇩🇪    | 是   | 由個人提供，攔截廣告、跟蹤器和惡意軟體                           | [DoH/DoT][blahdns-profile]          |
| [BlahDNS 日本][blahdns]                          | 🇯🇵    | 是   | 由個人提供，攔截廣告、跟蹤器和惡意軟體                           | [DoH/DoT][blahdns-profile]          |
| [BlahDNS 新加坡][blahdns]                        | 🇸🇬    | 是   | 由個人提供，攔截廣告、跟蹤器和惡意軟體                           | [DoH/DoT][blahdns-profile]          |
| [BlahDNS 瑞士][blahdns]                          | 🇨🇭    | 是   | 由個人提供，攔截廣告、跟蹤器和惡意軟體                           | [DoH/DoT][blahdns-profile]          |
| [Canadian Shield 隱私][canadian-shield]          | 🇨🇦    | 否   | 由加拿大網路註冊局 (CIRA) 運營                                   | [DoH/DoT][canadian-shield-profile]  |
| [Canadian Shield 保護][canadian-shield]          | 🇨🇦    | 是   | 由加拿大網路註冊局 (CIRA) 運營，攔截惡意軟體和釣魚網站           | [DoH/DoT][canadian-shield-profile]  |
| [Canadian Shield 家庭][canadian-shield]          | 🇨🇦    | 是   | 由加拿大網路註冊局 (CIRA) 運營，攔截惡意軟體、釣魚網站和成人內容 | [DoH/DoT][canadian-shield-profile]  |
| [Cloudflare 1.1.1.1][cloudflare-dns]             | 🇺🇸    | 否   | 由 Cloudflare 運營                                               | [DoH/DoT][cloudflare-dns-profile]   |
| [Cloudflare 1.1.1.1 安全][cloudflare-dns-family] | 🇺🇸    | 是   | 由 Cloudflare 運營，攔截惡意軟體和釣魚網站                       | [DoH/DoT][cloudflare-dns-profile]   |
| [Cloudflare 1.1.1.1 家庭][cloudflare-dns-family] | 🇺🇸    | 是   | 由 Cloudflare 運營，攔截惡意軟體、釣魚網站和成人內容             | [DoH/DoT][cloudflare-dns-profile]   |
| [DNSPod 公共 DNS][dnspod-dns]                    | 🇨🇳    | 否   | 由騰訊雲計算旗下 DNSPod 運營                                     | [DoH/DoT][dnspod-dns-profile]       |
| [Google 公共 DNS][google-dns]                    | 🇺🇸    | 否   | 由 Google 運營                                                   | [DoH/DoT][google-dns-profile]       |
| [keweonDNS][keweondns]                           | 🇩🇪    | 否   | 由 Aviontex. 攔截廣告和跟蹤器                                    | [DoH/DoT][keweondns-profile]        |
| [Mullvad DNS][mullvad-dns]                       | 🇸🇪    | 是   | 由 Mullvad VPN 運營                                              | [DoH/DoT][mullvad-dns-profile]      |
| [Mullvad DNS 廣告過濾][mullvad-dns]              | 🇸🇪    | 是   | 由 Mullvad VPN 運營，攔截廣告和跟蹤器                            | [DoH/DoT][mullvad-dns-profile]      |
| [NextDNS][nextdns]                               | 🇺🇸    | 否   | 由 NextDNS 運營，可客製化攔截                                    | [DoH/DoT][nextdns-profile]          |
| [OpenDNS 標準][opendns]                          | 🇺🇸    | 否   | 由思科 OpenDNS 運營                                              | [DoH][opendns-profile]              |
| [OpenDNS 家庭防護][opendns]                      | 🇺🇸    | 是   | 由思科 OpenDNS 運營，攔截惡意軟體和成人內容                      | [DoH][opendns-profile]              |
| [Quad9][quad9-dns]                               | 🇨🇭    | 是   | 由 Quad9 基金會運營，攔截惡意軟體                                | [DoH/DoT][quad9-dns-profile]        |
| [Quad9 ECS][quad9-dns]                           | 🇨🇭    | 是   | 由 Quad9 基金會運營，支持 ECS，攔截惡意軟體                      | [DoH/DoT][quad9-dns-profile]        |
| [Quad101][quad101-dns]                           | 🇹🇼    | 否   | 由台灣網路資訊中心 (TWNIC) 運營                                  | [DoH/DoT][quad101-dns-profile]      |
| [Tiarap][tiarap-dns]                             | 🇸🇬 🇺🇸 | 是   | 由 Tiarap 運營，攔截廣告、跟蹤器、釣魚網站和惡意軟體             | [DoH/DoT][tiarap-dns-profile]       |

## 安裝

要使設置在 **iOS**、**iPadOS** 和 **macOS** 中所有的應用程式上生效，你需要安裝設定描述檔。此文件將指引操作系統使用 DoH 或 DoT。注意：僅在系統 Wi-Fi 設定中設置 DNS 伺服器 IP 是不夠的——你需要安裝描述檔。

iOS / iPadOS：使用 Safari 瀏覽器（其他瀏覽器只會下載該文件，不會彈出安裝提示）打開 GitHub 上的 mobileconfig 文件，然後點擊「允許」按鈕，描述檔將完成下載。打開 **系統設定 => 一般 => VPN、DNS 與裝置管理**，選擇已下載的描述檔並點擊「安裝」按鈕。

macOS [（官方文檔）](https://support.apple.com/zh-tw/guide/mac-help/mh35561/)：

1. 下載並保存描述檔，將其重命名為 `NAME.mobileconfig`，而不是 txt 之類的副檔名。
2. 選擇「蘋果」選單 >「系統設定」，按一下側邊欄中的「隱私權和安全性」，然後按一下右側的「描述檔」。（你可能需要向下捲動。）
   安裝期間，系統可能會要求你提供密碼或其他資訊。
3. 在「已下載」區域中，按兩下描述檔。
4. 檢視描述檔內容然後按一下「繼續」、「安裝」或「註冊」來安裝描述檔。

   若 Mac 上已安裝描述檔的較早版本，則以上版本中的設定會取代先前的設定。

## 生效範圍

目前所有的描述檔都被配置為系統全局範圍生效，如果你想嘗試用戶範圍生效，請將描述檔中下面兩行內容刪除，或將 `System` 改為 `User`。

```xml
<key>PayloadScope</key>
<string>System</string>
```

## 簽署版描述檔

目前沒有提供任何簽署版的描述檔，如果你對描述檔安裝界面的綠色簽署認證圖示有執念，可以考慮前往[這裡](https://github.com/paulmillr/encrypted-dns/tree/master/signed)下載由 [@Candygoblen123](https://github.com/Candygoblen123) 提供的簽署版描述檔，但內容可能會更新不及時。

如要驗證 DNS 解析器的 IP 和主機名，請將描述檔內容與其官方網站的文檔進行比對，描述檔內部結構和屬性在[蘋果開發人員網站](https://developer.apple.com/documentation/devicemanagement/dnssettings)上有詳細講解。如要驗證簽署版的描述檔，請將其下載到本地後用文字編輯器打開，因為 GitHub 會將簽署版描述檔視為二進位檔案而無法直接查看。

## 創建新描述檔

你可以使用這個[工具](https://dns.notjakob.com/tool.html)在線創建你自己的描述檔。

描述檔本質上是 XML 文字檔案，如果你有興趣提交新的描述檔，將現有的描述檔複製一份並修改其 UUID 即可，請確保在本 README 文件中更新描述檔的相關訊息。

隨機 UUID 除了可以通過網站在線生成，還有很多其他獲取方法：

- 在瀏覽器中按下 `F12` 打開“開發人員工具”，在主控台中執行這段程式碼

```javascript
crypto.randomUUID();
```

- 在 macOS / Linux 終端機中執行此指令

```sh
# 適用於 macOS 和 Linux
uuidgen

# 適用於 Linux
cat /proc/sys/kernel/random/uuid
```

- 在 Powershell 中執行此指令

```powershell
New-Guid
```

[360-security-dns]: https://sdns.360.net/dnsPublic.html
[360-security-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/360-security-dns.mobileconfig
[adguard-dns-default]: https://adguard-dns.io/kb/general/dns-providers/#default
[adguard-dns-family]: https://adguard-dns.io/kb/general/dns-providers/#family-protection
[adguard-dns-unfiltered]: https://adguard-dns.io/kb/general/dns-providers/#non-filtering
[adguard-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/adguard-dns.mobileconfig
[alekberg-dns]: https://alekberg.net
[alekberg-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/alekberg-dns.mobileconfig
[aliyun-dns]: https://www.alidns.com/
[aliyun-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/aliyun-dns.mobileconfig
[blahdns]: https://blahdns.com/
[blahdns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/blahdns.mobileconfig
[canadian-shield]: https://www.cira.ca/cybersecurity-services/canadian-shield/configure/summary-cira-canadian-shield-dns-resolver-addresses
[canadian-shield-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/canadian-shield.mobileconfig
[cloudflare-dns]: https://developers.cloudflare.com/1.1.1.1/encryption/
[cloudflare-dns-family]: https://developers.cloudflare.com/1.1.1.1/setup/#1111-for-families
[cloudflare-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/cloudflare-dns.mobileconfig
[dnspod-dns]: https://www.dnspod.cn/products/publicdns
[dnspod-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/dnspod-dns.mobileconfig
[google-dns]: https://developers.google.com/speed/public-dns/docs/secure-transports
[google-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/google-dns.mobileconfig
[keweondns]: https://forum.xda-developers.com/t/keweondns-info-facts-and-what-is-keweon-actually.4576651/
[keweondns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/keweondns.mobileconfig
[mullvad-dns]: https://mullvad.net/help/dns-over-https-and-dns-over-tls/
[mullvad-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/mullvad-dns.mobileconfig
[nextdns]: https://nextdns.io/
[nextdns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/nextdns.mobileconfig
[opendns]: https://support.opendns.com/hc/articles/360038086532
[opendns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/opendns.mobileconfig
[quad9-dns]: https://www.quad9.net/news/blog/doh-with-quad9-dns-servers/
[quad9-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/quad9-dns.mobileconfig
[quad101-dns]: https://101.101.101.101/
[quad101-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/quad101-dns.mobileconfig
[tiarap-dns]: https://doh.tiar.app
[tiarap-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/tiarap-dns.mobileconfig
