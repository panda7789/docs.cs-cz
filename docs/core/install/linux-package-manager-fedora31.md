---
title: Instalace .NET Core na Fedoru 31 - správce balíčků - .NET Core
description: Pomocí správce balíčků nainstalujte na Fedoru 31 .NET Core SDK a runtime.
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 28bda3676f99037e565080e1ff3f9d89a67d0d69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920785"
---
# <a name="fedora-31-package-manager---install-net-core"></a>Správce balíčků Fedora 31 – instalace jádra .NET

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na Fedoru 31. Pokud instalujete runtime, doporučujeme nainstalovat [ASP.NET core runtime](#install-the-aspnet-core-runtime), protože zahrnuje rozhraní .NET Core i ASP.NET Core runtime.

## <a name="register-microsoft-key-and-feed"></a>Registrace klíče Microsoft a informačního kanálu

Před instalací rozhraní .NET budete muset:

- Zaregistrujte klíč Společnosti Microsoft.
- Zaregistrujte úložiště produktů.
- Nainstalujte požadované závislosti.

Stačí to provést jednou na jednom počítači.

Otevřete terminál a spusťte následující příkazy.

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a>Nainstalujte sadu .NET Core SDK.

Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte sadu .NET Core SDK. V terminálu spusťte následující příkaz.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Instalace core runtime

Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte ASP.NET runtime. V terminálu spusťte následující příkaz.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalace runtime jádra .NET

Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte za běhu .NET Core. V terminálu spusťte následující příkaz.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Poradce při potížích se správcem balíčků

Tato část obsahuje informace o běžných chybách, které se mohou stát při instalaci rozhraní .NET Core pomocí správce balíčků.

### <a name="failed-to-fetch"></a>Načtení se nezdařilo.

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
