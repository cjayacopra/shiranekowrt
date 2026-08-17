# ShiranekoWrt

ShiranekoWrt is a ready-to-use operating system for the **Arcadyan AW1000** — the 5G WiFi router it comes with. Think of it like the Android or iOS of routers: it's the software that makes your router work. It's built on **OpenWrt 25.12**, the newest, most up-to-date foundation available.

---

## First Boot — Quick Start

When you first turn the router on, everything you need to get online is already set up:

| Setting                           | Default Value                                                   |
| --------------------------------- | --------------------------------------------------------------- |
| Router address                    | `10.10.10.1` (or `http://shiranekowrt/` in a browser)           |
| Login name                        | `root`                                                          |
| Password                          | _(none set — the router asks you to create one on first login)_ |
| WiFi name (5 GHz, faster)         | `ShiranekoWrt 5G`                                               |
| WiFi name (2.4 GHz, longer range) | `ShiranekoWrt`                                                  |
| WiFi password                     | `wireless123@ShiranekoWrt`                                      |

Once powered on, the router **automatically detects the built-in 5G modem**, connects to the mobile network, and turns on your WiFi. The lights on the front tell you what it's doing at every step (see [Understanding the Lights](#understanding-the-lights)).

---

## Using Your Router

### The Control Panel

Your router has a built-in **control panel** (a website the router hosts itself). To open it, connect any device to the WiFi (or plug in a cable) and visit `http://10.10.10.1/` in your web browser — or simply type `http://shiranekowrt/`, which works the same way. Log in with the user name `root` — the first time you visit, the router will ask you to create a password for it.

Across the top of the control panel there's a **toolbar** with shortcuts to the most-used pages:

- **Network** — see and manage your internet connection, the network behind the router, and connected devices
- **WiFi** — change your WiFi names and passwords, switch channels, and adjust wireless settings
- **Modem Status** — detailed information about your 5G connection: signal strength, network type (5G/4G), which cell tower you're on, and your data usage
- **QModem** — manage the SIM card and the cellular connection itself, and send/receive **SMS text messages** right from the control panel
- **Xray** — a tool for advanced users to route internet traffic through a private tunnel (works with VLESS, VMess, Trojan, Shadowsocks, and more)
- **Bandix** — live charts of your internet traffic and how much bandwidth each device is using
- **Firmware Update** — update the router in one click (more below)

There's also a **search box** across the top of the control panel to find any setting instantly.

### Pick Your Look

ShiranekoWrt comes with **three themes**, switchable anytime from **System → Theme Configuration**:

1. **Aurora** (default) — a modern look with light/dark modes, custom colours and fonts, a mega-menu, and a "phone app" mode (install the control panel on your phone's home screen). The default look uses a **custom preset** ShiranekoWrt ships with, inspired by the **Kanagawa Dragon/Lotus** colour palette — the warm paper-toned light mode and the deep, moody dark mode you see on first boot.
2. **Bootstrap** — the classic, familiar router layout, simple and clean.
3. **Footstrap** — a clean, lightweight classic layout, simple and easy to read.

**Not a fan of the default look?** You're in full control. Aurora has **several official presets** built in (like Sage Green, Amber Sand, Sky Blue, and Monochrome), each with its own colours, layout shape, and typography — just pick one from the theme settings. Beyond that, Aurora has a **Theme Store** where you can **browse and install complete themes** made by others, fonts included. Nothing is locked down: you can go as deep as you like — tweak individual colours, upload your own fonts, change the layout, add a wallpaper, even upload a custom logo. ShiranekoWrt only sets the starting look; what it becomes is entirely up to you.

### Modem & Cellular Tools

The built-in 5G modem works out of the box:

- **Automatic connection** — the modem connects to your mobile network every time the router turns on
- **Signal information** — see your signal strength, which network type you're on (5G standalone, 5G, 4G, 3G), the cell tower you're connected to, your operator's name, and data usage
- **SMS** — send and receive text messages through the control panel

### Watching Your Internet

- **Bandix** — see live speed graphs and which device is using the most bandwidth
- **Speed widget** — the main status page shows a live download/upload speed meter (this reflects real traffic on your connection)
- **Disk Info** — if you plug in a USB drive, see its health, partitions, and temperature

### USB Storage & File Sharing

Plug in a USB drive and ShiranekoWrt can:

- Recognise and mount it automatically
- **Share its files over your network** — the control panel has a **System → Samba** page where you create a shared folder, give it a name, and choose who can see it. This is the option most devices (Windows, Android, smart TVs) understand best.
- **NFS sharing** is also included for advanced setups. It ships with a **template** export file (`/etc/exports`) that you adapt to your own drives and network — it is **not** a ready-to-use share out of the box, and it has no settings page in the control panel. For detailed setup guides, see the [OpenWrt NFS documentation](https://openwrt.org/docs/guide-user/services/nfs) and the [Arch Linux NFSv4 wiki](https://wiki.archlinux.org/title/NFS)
- Has a built-in **drive sleep** setting (available in the control panel's Storage tools) that parks idle drives to save power and extend drive life

### Updating the Router

No need to hunt for files or use complicated commands. The **Firmware Update** page:

1. Checks the project's page for the newest release
2. Downloads it for you
3. Asks whether you want to **keep your settings** or **start fresh**
4. Upgrades the router and reboots it automatically

---

## Understanding the Lights

The lights on the front of the router are its way of talking to you. Here's what they mean:

### During Startup

| What You'll See                                | What's Happening                                       |
| ---------------------------------------------- | ------------------------------------------------------ |
| Power on, signal light **white**, 5G off       | Router is starting up                                  |
| Power on, signal light **white**, 5G off       | SIM card found, waiting for it to be ready (e.g., PIN) |
| Power on, signal light **amber**, 5G **amber** | Modem is connecting to the network                     |
| Power on, **colour-coded lights**              | Connected and working                                  |

### Once Connected

| Light                     | Meaning                                                                                                       |
| ------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Signal** (multi-colour) | **Green** = strong signal, **Blue** = medium, **Red** = weak                                                  |
| **5G** (multi-colour)     | **White** = 5G standalone, **Green** = 5G, **Blue** = 4G, **Red** = 3G                                        |
| **Internet**              | Blinks when data is flowing, steady when idle                                                                 |
| **WiFi**                  | **Steady** = both WiFi bands on, **fast blink** = only the 5 GHz band, **slow blink** = only the 2.4 GHz band |
| **Phone**                 | **Steady** = SIM ready, **blinks for ~30 seconds** = a new text message arrived                               |
| **Power**                 | Steady = the router is running                                                                                |

---

## A Few Things to Know

- **It's fast** — Gigabit speeds on the wired ports and near-Gigabit on WiFi.
- **IPv6 is turned off.** Most home connections don't need it, and it keeps things simple.
- **The router manages your "phone book" for the internet.** It automatically handles the service that translates website names (like `example.com`) into addresses. If you use a custom DNS service (for example, a Pi-hole), you can change this under **Network → DHCP Server**.
- **All 5 ports on the back are one big network.** Whether you plug your internet cable or a computer into LAN1 or WAN, it works the same way.
- **Some software shortcuts are intentionally switched off** so the router's built-in hardware accelerator can do its job properly — this is what makes it fast without overheating. You don't need to touch these.

---

## ⚠️ Before You Flash: An Important Safety Check

ShiranekoWrt has **only been tested with the "Expanded" storage layout** described in this guide:
[Expanded MTD layout guide](https://github.com/ChamodyaChiran/AW1000-NSS-Build-Public/blob/main/Expanded%20MTD%20layout.md)

Flashing ShiranekoWrt onto a router that does **not** have the expanded layout can **permanently damage the router**. Please do not flash unless you're sure your router already has it.

### How to Check Before Flashing

Open a terminal (or SSH) on your router and run:

```
cat /proc/mtd | grep '"rootfs"$'
```

- If you see something like:

  ```
  mtd18: 06400000 00040000 "rootfs"
  ```

  you have the **Standard** layout (~100 MB) — **do not flash ShiranekoWrt yet**. Apply the expanded layout first.

- If you see something like:
  ```
  mtd24: 2bd00000 00040000 "rootfs"
  ```
  you have the **Expanded** layout (~701 MB) — you're good to go.

---

## Set Your Time Zone & WiFi Country

No matter where you live, set two things after first boot: your **time zone** and your **WiFi country code**. The router does not assume any region by default.

| Setting           | Default                                                              | Where to Change It                                                         |
| ----------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Time zone**     | UTC                                                                  | **System → System → Time zone**                                            |
| **WiFi country**  | Not set — choose your own                                            | **Network → Wireless → Edit a network → Advanced Settings → Country Code** |
| **WiFi channels** | Automatic (5 GHz: UNII-3 channels 149/153/157/161 · 2.4 GHz: 1/6/11) | **Network → Wireless → Edit a network → Channel**                          |

Setting your **WiFi country** is the most important one — until you set one, WiFi only uses the default channel list above, which may not include the channels and power levels that are legal in your region. Setting the country makes the router use the right channels and power automatically.

---

## Default Passwords

| What                | Username | Password                                                |
| ------------------- | -------- | ------------------------------------------------------- |
| Control panel / SSH | `root`   | _(none — you'll be asked to create one on first login)_ |
| WiFi (both bands)   | —        | `wireless123@ShiranekoWrt`                              |

**Please set a `root` password** the first time you log in — the router will prompt you on the opening screen (**System → Administration** also works). It's the only thing protecting your router from strangers.

---

## Credits

ShiranekoWrt would not exist without these projects and their authors:

| Project / Author                        | Contribution                                                                                                                                                                                   |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[OpenWrt](https://openwrt.org)**      | The core operating system and build system this firmware is built on                                                                                                                           |
| **[qosmio](https://github.com/qosmio)** | The NSS packages and foundational work that enable hardware-accelerated networking on this chipset                                                                                             |
| **[FuJr](https://github.com/FUjr)**     | QModem — the framework that manages the cellular connection, SMS, and the front lights                                                                                                         |
| **eamonxg**                             | [luci-theme-aurora](https://github.com/eamonxg/luci-theme-aurora) and [luci-app-aurora-config](https://github.com/eamonxg/luci-app-aurora-config) — the modern theme and its customisation app |
| **gSpotx2f**                            | [luci-app-disks-info](https://github.com/gSpotx2f/luci-app-disks-info) — USB drive health and info                                                                                             |
| **yichya**                              | [luci-app-xray](https://github.com/yichya/luci-app-xray) and Xray-core packaging                                                                                                               |
| **Rafał Wabik (IceG)**                  | [modemdata](https://eko.one.pl/) and [luci-app-modemdata](https://github.com/iceg/luci-app-modemdata) — the modem signal/diagnostics pages                                                     |
| **smallprogram**                        | [openwrt-ghfu](https://github.com/smallprogram/openwrt-ghfu) — the one-click firmware update page                                                                                              |
| **timsaya**                             | [bandix](https://github.com/timsaya/bandix) and [luci-app-bandix](https://github.com/timsaya/luci-app-bandix) — live traffic monitoring                                                        |
| **Cezary Jackiewicz**                   | Original modemdata utility                                                                                                                                                                     |
| **XTLS**                                | [Xray-core](https://github.com/XTLS/Xray-core) — the engine powering the Xray page                                                                                                             |
| **ChamodyaChiran**                      | The Expanded storage layout guide for the AW1000                                                                                                                                               |
| **LuCI community**                      | All the module and theme authors whose work makes the control panel possible                                                                                                                   |

Thank you to the entire OpenWrt community for making this possible.

---

## Disclaimer

This firmware is provided **as-is, without any warranty of any kind**, express or implied. Use it **at your own risk**. The authors are not responsible for any damage, data loss, or bricked devices resulting from its use.
