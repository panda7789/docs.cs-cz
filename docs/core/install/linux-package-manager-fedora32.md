---
title: Instalace .NET Core v Fedora 32 – Správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v Fedora 32.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624964"
---
# <a name="fedora-32-package-manager---install-net-core"></a>Správce balíčků Fedora 32 – instalace .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Fedora 32.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

Od Fedora 32 je .NET Core 3,1 k dispozici ve výchozích úložištích balíčků v Fedora.

## <a name="install-the-net-core-sdk"></a>Nainstalujte sadu .NET Core SDK.

Nainstalujte .NET Core SDK. V terminálu spusťte následující příkaz.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalace modulu runtime ASP.NET Core

Nainstalujte modul runtime ASP.NET. V terminálu spusťte následující příkaz.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalace modulu runtime .NET Core

Nainstalujte modul runtime .NET Core. V terminálu spusťte následující příkaz.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

Pokud chcete nainstalovat další verze .NET Core, nainstalujte [.NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) nebo [modul runtime .NET Core](runtime.md?pivots=os-linux#download-and-manually-install)ručně.
