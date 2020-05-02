---
title: Nainstalovat .NET Core na Linux CentOS 8 Package Manager – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v CentOS 8.
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: b4cf5975e18aa8dfa8649c0d038caf38d648ad86
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728517"
---
# <a name="centos-8-package-manager---install-net-core"></a>Správce balíčků CentOS 8 – instalace .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na CentOS 8.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="install-the-net-core-sdk"></a>Nainstalujte sadu .NET Core SDK.

V terminálu spusťte následující příkaz.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalace modulu runtime ASP.NET Core

V terminálu spusťte následující příkaz.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalace modulu runtime .NET Core

V terminálu spusťte následující příkaz.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
