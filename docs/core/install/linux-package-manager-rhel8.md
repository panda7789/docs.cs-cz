---
title: Nainstalovat .NET Core na Linux RHEL 8 Package Manager – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: 8829e842e920e6abd4184b5140f80bb016acace2
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728232"
---
# <a name="rhel-8-package-manager---install-net-core"></a>Správce balíčků RHEL 8 – instalace .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Red Hat Enterprise Linux (RHEL) 8.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Zaregistrujte si předplatné Red Hat

Pokud chcete nainstalovat .NET Core ze Red Hat na RHEL, musíte se nejdřív zaregistrovat pomocí Správce předplatných Red Hat. Pokud jste to ještě neudělali v systému nebo pokud si nejste jistí, přečtěte si část [dokumentace k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Nainstalujte sadu .NET Core SDK.

Po registraci pomocí Správce předplatného můžete nainstalovat a povolit .NET Core SDK. V terminálu spusťte následující příkaz.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalace modulu runtime ASP.NET Core

Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime ASP.NET Core. V terminálu spusťte následující příkaz.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalace modulu runtime .NET Core

Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime .NET Core. V terminálu spusťte následující příkaz.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="see-also"></a>Viz také

- [Použití .NET Core 3,1 na Red Hat Enterprise Linux 8](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
