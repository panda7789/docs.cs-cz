---
title: Nainstalovat .NET Core na Linux RHEL 8,1 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 8674b5d9d0f0ee384ca6798a7ea699bad67c5e5e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341195"
---
# <a name="rhel-81-package-manager---install-net-core"></a>Správce balíčků RHEL 8,1 – instalace .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na RHEL 8,1. .NET Core 3,1 není ještě k dispozici pro RHEL 8,1.

> [!NOTE]
> RHEL 8,0 nezahrnuje .NET Core 3,0. K aktualizaci na RHEL 8,1 použijte příkaz `yum upgrade`.

## <a name="register-your-red-hat-subscription"></a>Zaregistrujte si předplatné Red Hat

Pokud chcete nainstalovat .NET Core ze Red Hat na RHEL, musíte se nejdřív zaregistrovat pomocí Správce předplatných Red Hat. Pokud jste to ještě neudělali v systému nebo pokud si nejste jistí, přečtěte si část [dokumentace k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Instalace .NET Core SDK

Po registraci pomocí Správce předplatného můžete nainstalovat a povolit .NET Core SDK. V terminálu spusťte následující příkazy.

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Instalace modulu runtime ASP.NET Core

Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime ASP.NET Core. V terminálu spusťte následující příkazy.

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a>Instalace modulu runtime .NET Core

Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime .NET Core. V terminálu spusťte následující příkazy.

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a>Viz také:

- [Použití .NET Core 3,0 na Red Hat Enterprise Linux 8](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
