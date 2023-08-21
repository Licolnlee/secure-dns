English | [简体中文](https://github.com/francis-zhao/secure-dns/blob/master/README.cmn-CN.md) | [繁體中文](https://github.com/francis-zhao/secure-dns/blob/master/README.cmn-TW.md)

# Secure DNS

## Intro

This repo is a fork of [paulmillr/encrypted-dns](https://github.com/paulmillr/encrypted-dns). It contains configuration profiles of [DNS over HTTPS (DoH)](https://en.wikipedia.org/wiki/DNS_over_HTTPS) and [DNS over TLS (DoT)](https://en.wikipedia.org/wiki/DNS_over_TLS) for Apple devices.

Compared with the original repo, all profiles of this fork have been reassigned unique UUIDs, and all DoH and DoT configurations of the same provider are integrated in one file, which makes it easier to switch and manage in the system settings.

### Caveats

On devices that support HTTP/3, DNS over HTTP/3 (DoH3) seems to work faster & better than DoT judging from the [Google's article](https://security.googleblog.com/2022/07/dns-over-http3-in-android.html).

Starting from iOS & iPadOS 15.5, [Wi-Fi captive portals](https://en.wikipedia.org/wiki/Captive_portal) in cafes, hotels, airports are exempted by Apple from eDNS rules; to simplify authentication. This is good news. There are still some other issues; we can't fix them, only Apple can:

- eDNS gets disabled: [Little Snitch & Lulu](https://github.com/paulmillr/encrypted-dns/issues/13), [VPN](https://github.com/paulmillr/encrypted-dns/issues/18)
- Some traffic is exempt from eDNS: [Terminal / App Store](https://github.com/paulmillr/encrypted-dns/issues/22), [Chrome](https://github.com/paulmillr/encrypted-dns/issues/19)

If you need even more privacy, check out [encrypted-dns over TOR](https://github.com/alecmuffett/dohot).

## Providers

`Censorship=yes` means the profile will not send true information about `hostname=IP` relation for some hosts.

| Name                                                 | Region | Censorship | Notes                                                                                                     | Install link                        |
| ---------------------------------------------------- | ------ | ---------- | --------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| [360 Security DNS][360-security-dns]                 | 🇨🇳     | Yes        | Operated by 360 Digital Security Group                                                                    | [DoH/DoT][360-security-dns-profile] |
| [AdGuard DNS Default][adguard-dns-default]           | 🇷🇺     | Yes        | Operated by AdGuard Software Ltd. Blocks ads, tracking & phishing                                         | [DoH/DoT][adguard-dns-profile]      |
| [AdGuard DNS Family Protection][adguard-dns-family]  | 🇷🇺     | Yes        | Operated by AdGuard Software Ltd. Blocks `Default` + malware & adult content                              | [DoH/DoT][adguard-dns-profile]      |
| [AdGuard DNS Non-filtering][adguard-dns-unfiltered]  | 🇷🇺     | No         | Operated by AdGuard Software Ltd. Non-filtering                                                           | [DoH/DoT][adguard-dns-profile]      |
| [Alekberg Encrypted DNS][alekberg-dns]               | 🇳🇱     | No         | Independent                                                                                               | [DoH][alekberg-dns-profile]         |
| [Aliyun Public DNS][aliyun-dns]                      | 🇨🇳     | No         | Operated by Alibaba Cloud Ltd.                                                                            | [DoH/DoT][aliyun-dns-profile]       |
| [BlahDNS CDN Filtered][blahdns]                      | 🇺🇸     | Yes        | Independent. Blocks ads, tracking & malware                                                               | [DoH/DoT][blahdns-profile]          |
| [BlahDNS CDN Unfiltered][blahdns]                    | 🇺🇸     | No         | Independent. Non-filtering                                                                                | [DoH/DoT][blahdns-profile]          |
| [BlahDNS Finland][blahdns]                           | 🇫🇮     | Yes        | Independent. Blocks ads, tracking & malware                                                               | [DoH/DoT][blahdns-profile]          |
| [BlahDNS Germany][blahdns]                           | 🇩🇪     | Yes        | Independent. Blocks ads, tracking & malware                                                               | [DoH/DoT][blahdns-profile]          |
| [BlahDNS Japan][blahdns]                             | 🇯🇵     | Yes        | Independent. Blocks ads, tracking & malware                                                               | [DoH/DoT][blahdns-profile]          |
| [BlahDNS Singapore][blahdns]                         | 🇸🇬     | Yes        | Independent. Blocks ads, tracking & malware                                                               | [DoH/DoT][blahdns-profile]          |
| [BlahDNS Switzerland][blahdns]                       | 🇨🇭     | Yes        | Independent. Blocks ads, tracking & malware                                                               | [DoH/DoT][blahdns-profile]          |
| [Canadian Shield Private][canadian-shield]           | 🇨🇦     | No         | Operated by the Canadian Internet Registration Authority (CIRA)                                           | [DoH/DoT][canadian-shield-profile]  |
| [Canadian Shield Protected][canadian-shield]         | 🇨🇦     | Yes        | Operated by the Canadian Internet Registration Authority (CIRA). Blocks malware & phishing                | [DoH/DoT][canadian-shield-profile]  |
| [Canadian Shield Family][canadian-shield]            | 🇨🇦     | Yes        | Operated by the Canadian Internet Registration Authority (CIRA). Blocks malware, phishing & adult content | [DoH/DoT][canadian-shield-profile]  |
| [Cloudflare 1.1.1.1][cloudflare-dns]                 | 🇺🇸     | No         | Operated by Cloudflare Inc.                                                                               | [DoH/DoT][cloudflare-dns-profile]   |
| [Cloudflare 1.1.1.1 Security][cloudflare-dns-family] | 🇺🇸     | Yes        | Operated by Cloudflare Inc. Blocks malware & phishing                                                     | [DoH/DoT][cloudflare-dns-profile]   |
| [Cloudflare 1.1.1.1 Family][cloudflare-dns-family]   | 🇺🇸     | Yes        | Operated by Cloudflare Inc. Blocks malware, phishing & adult content                                      | [DoH/DoT][cloudflare-dns-profile]   |
| [DNSPod Public DNS][dnspod-dns]                      | 🇨🇳     | No         | Operated by DNSPod Inc., a Tencent Cloud Company                                                          | [DoH/DoT][dnspod-dns-profile]       |
| [Google Public DNS][google-dns]                      | 🇺🇸     | No         | Operated by Google LLC                                                                                    | [DoH/DoT][google-dns-profile]       |
| [keweonDNS][keweondns]                               | 🇩🇪     | No         | Operated by Aviontex. Blocks ads & tracking                                                               | [DoH/DoT][keweondns-profile]        |
| [Mullvad DNS][mullvad-dns]                           | 🇸🇪     | Yes        | Operated by Mullvad VPN AB                                                                                | [DoH/DoT][mullvad-dns-profile]      |
| [Mullvad DNS Adblock][mullvad-dns]                   | 🇸🇪     | Yes        | Operated by Mullvad VPN AB. Blocks ads & tracking                                                         | [DoH/DoT][mullvad-dns-profile]      |
| [NextDNS][nextdns]                                   | 🇺🇸     | No         | Operated by NextDNS Inc. Customizable                                                                     | [DoH/DoT][nextdns-profile]          |
| [OpenDNS Standard][opendns]                          | 🇺🇸     | No         | Operated by Cisco OpenDNS LLC                                                                             | [DoH][opendns-profile]              |
| [OpenDNS FamilyShield][opendns]                      | 🇺🇸     | Yes        | Operated by Cisco OpenDNS LLC. Blocks malware & adult content                                             | [DoH][opendns-profile]              |
| [Quad9][quad9-dns]                                   | 🇨🇭     | Yes        | Operated by Quad9 Foundation. Blocks malware                                                              | [DoH/DoT][quad9-dns-profile]        |
| [Quad9 w/ ECS][quad9-dns]                            | 🇨🇭     | Yes        | Operated by Quad9 Foundation. Supports ECS. Blocks malware                                                | [DoH/DoT][quad9-dns-profile]        |
| [Quad101][quad101-dns]                               | 🇹🇼     | No         | Operated by Taiwan Network Information Center (TWNIC)                                                     | [DoH/DoT][quad101-dns-profile]      |
| [Tiarap][tiarap-dns]                                 | 🇸🇬 🇺🇸  | Yes        | Operated by Tiarap Inc. Blocks ads, tracking, phising & malware                                           | [DoH/DoT][tiarap-dns-profile]       |

## Installation

To make settings work across all apps in **iOS**, **iPadOS** & **macOS**, you'll need to install configuration profile. This profile would tell operating system to use DoH / DoT. Note: it's not enough to simply set server IPs in System Preferences — you need to install a profile.

iOS / iPadOS: Open the mobileconfig file in GitHub by using Safari (other browsers will just download the file and won't ask for installation), and then click/tap on "Allow" button. The profile should download. Go to **System Settings => General => VPN, DNS & Device Management**, select downloaded profile and tap the "Install" button.

macOS [(official docs)](https://support.apple.com/guide/mac-help/mh35561/):

1. Download and save the profile. After save, rename it to be in format: `NAME.mobileconfig`, not NAME.txt, or so
2. Choose Apple menu > System Settings, click Privacy and Security in the sidebar, then click Profiles on the right. (You may need to scroll down.)
   You may be asked to supply your password or other information during installation.
3. In the Downloaded section, double-click the profile.
4. Review the profile contents then click Continue, Install or Enroll to install the profile.

   If an earlier version of a profile is already installed on your Mac, the settings in the updated version replace the previous ones.

## Scope

Currently, all profiles are configured as system-wide, if you want to try user-wide, just delete the following two lines in the profile or change `System` to `User`.

```xml
<key>PayloadScope</key>
<string>System</string>
```

## Signed Profiles

At present, no signed version profiles is provided. If you are obsessed with the green authentication icon on the installation popup, you may consider going [here](https://github.com/paulmillr/encrypted-dns/tree/master/signed) to download the signed version profiles provided by [@Candygoblen123](https://github.com/Candygoblen123), but the content may be slightly outdated.

To verify resolver IPs and hostnames, compare mobileconfig files to their documentation URLs. Internal workings of the profiles are described on [developer.apple.com](https://developer.apple.com/documentation/devicemanagement/dnssettings). In order to verify signed mobileconfigs, you will need to download them to your computer and open them in a text editor, because signing profiles makes GitHub think that they are binary files.

## Creating a new profile

You can use [this tool](https://dns.notjakob.com/tool.html) to create a personal profile online.

Profiles are basically XML text files. If you're interested in contributing a new profile, please copy an existing one and change its UUID, make sure you update README with new profile's info.

In addition to generating online, there are many other ways to generate a random UUID:

- Press `F12` to open DevTools in the browser, run this code in the console

```javascript
crypto.randomUUID();
```

- Run these commands in the macOS / Linux terminal

```sh
# Works both in macOS & Linux
uuidgen

# Works in Linux
cat /proc/sys/kernel/random/uuid
```

- Run this cmdlet in Powershell

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
[dnspod-dns]: https://www.dnspod.com/products/public.dns
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
[quad101-dns]: https://101.101.101.101/index_en.html
[quad101-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/quad101-dns.mobileconfig
[tiarap-dns]: https://doh.tiar.app
[tiarap-dns-profile]: https://github.com/francis-zhao/secure-dns/raw/master/profiles/tiarap-dns.mobileconfig
