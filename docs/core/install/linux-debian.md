---
title: Instalace .NET Core na Debian – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v Debian.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: d4a54a8a5354a1430141d2c06d4aa90dbafc3edf
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134936"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a>Instalace .NET Core SDK nebo modulu runtime .NET Core v Debian

Tento článek popisuje, jak nainstalovat .NET Core na Debian. Pokud je verze Debian mimo podporu, rozhraní .NET Core již není s touto verzí podporováno. Tyto pokyny vám ale můžou usnadnit práci s .NET Core na těchto verzích, i když není podporovaná.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Podporované distribuce

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze Debian, na kterých jsou podporované. Tato verze zůstane podporovaná, dokud žádná verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [Debian dosáhne konce životnosti](https://wiki.debian.org/DebianReleases).

- ✔️ označuje, že je stále podporovaná verze Debian nebo .NET Core.
- ❌Indikuje, že verze Debian nebo .NET Core není v této verzi Debian podporována.
- Pokud se ✔️á jak verze Debian, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| Debian                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (jenom ruční instalace) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](#debian-10-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [9](#debian-9-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌ [8](#debian-8-)       | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 Preview |

Následující verze rozhraní .NET Core již nejsou podporovány. Soubory ke stažení pro tyto soubory zůstanou publikované:

- 3,0
- 2,2
- 2,0

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a>Debian 10 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a>Debian 9 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-8-"></a>Debian 8 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a>APT Update SDK nebo modul runtime

Když je k dispozici nová verze opravy pro .NET Core, můžete ji jednoduše upgradovat prostřednictvím APT pomocí následujících příkazů:

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a>Řešení potíží s APT

V této části najdete informace o běžných chybách, ke kterým může dojít při použití APT k instalaci .NET Core.

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a>Nepovedlo se najít některé balíčky, které se \\ nedaly nainstalovat.

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a>Nepovedlo se načíst

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a>Moduly snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Závislosti

Při instalaci nástroje pomocí Správce balíčků se tyto knihovny nainstalují za vás. Pokud ale ručně nainstalujete rozhraní .NET Core nebo publikujete samostatnou aplikaci, musíte se ujistit, že jsou nainstalované tyto knihovny:

- libc6
- libgcc1
- libgssapi – krb5 – 2
- libicu52 (pro 8. x)
- libicu57 (pro 9. x)
- libicu63 (pro 10. x)
- libicu67 (pro 11. x)
- libssl 1.0.0 (pro 8. x)
- libssl 1.1 (pro 9. x-11. x)
- libstdc + + 6
- zlib1g

Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:

- libgdiplus (verze 6.0.1 nebo novější)

  > [!WARNING]
  > Můžete nainstalovat nejnovější verzi *libgdiplus* přidáním úložiště mono do systému. Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Skriptovaná instalace

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Ruční instalace

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Další kroky

- [Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md)
