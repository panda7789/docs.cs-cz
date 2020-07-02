---
title: Instalace .NET Core na openSUSE – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 24f0a5b5278d038c2f941b0984efcacd91dcbe31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619465"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a>Instalace .NET Core SDK nebo modulu runtime .NET Core v openSUSE

Rozhraní .NET Core je podporováno v openSUSE. Tento článek popisuje, jak nainstalovat .NET Core na openSUSE.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Podporované distribuce

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na openSUSE 15. Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze openSUSE.

- ✔️ označuje, že je stále podporovaná verze openSUSE nebo .NET Core.
- ❌Indikuje, že verze openSUSE nebo .NET Core není v této verzi openSUSE podporována.
- Pokud se ✔️á jak verze openSUSE, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| openSUSE                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (jenom ruční instalace) |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](#opensuse-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

Následující verze rozhraní .NET Core již nejsou podporovány. Soubory ke stažení pro tyto soubory zůstanou publikované:

- 3.0
- 2,2
- 2.0

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a>openSUSE 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a>Řešení potíží se správcem balíčků

V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.

### <a name="failed-to-fetch"></a>Nepovedlo se načíst

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a>Moduly snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Závislosti

Při instalaci nástroje pomocí Správce balíčků se tyto knihovny nainstalují za vás. Pokud ale ručně nainstalujete rozhraní .NET Core nebo publikujete samostatnou aplikaci, musíte se ujistit, že jsou nainstalované tyto knihovny:

- krb5
- libicu
- libopenssl1_0_0

Pokud je verze OpenSSL cílového běhového prostředí 1,1 nebo novější, budete muset nainstalovat **kompatibilní openssl10**.

Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:

- [libgdiplus (verze 6.0.1 nebo novější)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Můžete nainstalovat nejnovější verzi *libgdiplus* přidáním úložiště mono do systému. Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Skriptovaná instalace

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Ruční instalace

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Další kroky

- [Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md)
