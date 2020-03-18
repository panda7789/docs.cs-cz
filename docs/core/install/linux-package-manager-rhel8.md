---
title: Instalace .NET Core na Linux RHEL 8 správce balíčků - .NET Core
description: Pomocí správce balíčků nainstalujte sadu .NET Core SDK a runtime na RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 054494a9b77e1c7803e42c947e067d3eb290f73c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78849808"
---
# <a name="rhel-8-package-manager---install-net-core"></a>Správce balíčků RHEL 8 – instalace jádra .NET

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na RHEL 8.

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
