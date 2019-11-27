---
title: Nainstalovat .NET Core na Linux RHEL 8,1 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 5b658fe4c56b945210534872fe3cc502eb31a763
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450973"
---
# <a name="rhel-81-package-manager---install-net-core"></a>Správce balíčků RHEL 8,1 – instalace .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na RHEL 8,1.

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
