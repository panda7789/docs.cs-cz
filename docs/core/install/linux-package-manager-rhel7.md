---
title: Nainstalovat .NET Core na Linux RHEL 7 Package Manager – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: f17a410ccea1ef4dec32de1d80ef6aac889aa6f3
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836953"
---
# <a name="rhel-7-package-manager---install-net-core"></a>Správce balíčků RHEL 7 – instalace .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na RHEL 7. .NET Core 3,1 není zatím k dispozici pro RHEL 7.

## <a name="register-your-red-hat-subscription"></a>Zaregistrujte si předplatné Red Hat

Pokud chcete nainstalovat .NET Core ze Red Hat na RHEL, musíte se nejdřív zaregistrovat pomocí Správce předplatných Red Hat. Pokud jste to ještě neudělali v systému nebo pokud si nejste jistí, přečtěte si část [dokumentace k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Instalace .NET Core SDK

Po registraci pomocí Správce předplatného můžete nainstalovat a povolit .NET Core SDK. V terminálu spuštěním následujících příkazů povolte kanál dotnet RHEL 7 a nainstalujte.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Instalace modulu runtime ASP.NET Core

Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime ASP.NET Core. V terminálu spusťte následující příkazy.

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a>Instalace modulu runtime .NET Core

Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime .NET Core. V terminálu spusťte následující příkazy.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a>Viz také:

- [Použití .NET Core 3,0 na Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)
