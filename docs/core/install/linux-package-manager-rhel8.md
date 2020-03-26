---
title: Instalace .NET Core na Linux RHEL 8 správce balíčků - .NET Core
description: Pomocí správce balíčků nainstalujte sadu .NET Core SDK a runtime na RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b564a386eb67b6e414a832ad3bca10d3d09022bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134197"
---
# <a name="rhel-8-package-manager---install-net-core"></a>Správce balíčků RHEL 8 – instalace jádra .NET

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na RHEL 8.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Registrace předplatného Red Hatu

Chcete-li nainstalovat .NET Core z Red Hat na RHEL, musíte se nejprve zaregistrovat pomocí Správce předplatného Red Hat. Pokud se tak v systému nestalo nebo si nejste jisti, přečtěte si [dokumentaci k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Nainstalujte sadu .NET Core SDK.

Po registraci ve Správci předplatného jste připraveni k instalaci a povolení sady .NET Core SDK. V terminálu spusťte následující příkazy.

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalace ASP.NET Core Runtime

Po registraci u Správce předplatného jste připraveni nainstalovat a povolit ASP.NET Core Runtime. V terminálu spusťte následující příkazy.

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalace rozhraní .NET Core Runtime

Po registraci ve Správci předplatného jste připraveni k instalaci a povolení rozhraní .NET Core Runtime. V terminálu spusťte následující příkazy.

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a>Viz také

- [Použití rozhraní .NET Core 3.1 na Red Hat Enterprise Linux 8](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
