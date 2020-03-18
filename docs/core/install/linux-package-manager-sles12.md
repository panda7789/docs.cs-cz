---
title: Instalace .NET Core na SLES 12 - správce balíčků - .NET Core
description: Pomocí správce balíčků nainstalujte na sles 12 .NET Core SDK a runtime.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a6c10c6b11bc57ae4bbe814c66c563b85ce3c22b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920740"
---
# <a name="sles-12-package-manager---install-net-core"></a>SLES 12 Správce balíčků - instalace jádra .NET

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na SLES 12. Pokud instalujete runtime, doporučujeme nainstalovat [ASP.NET core runtime](#install-the-aspnet-core-runtime), protože zahrnuje rozhraní .NET Core i ASP.NET Core runtime.

## <a name="register-microsoft-key-and-feed"></a>Registrace klíče Microsoft a informačního kanálu

Před instalací rozhraní .NET budete muset:

- Zaregistrujte klíč Společnosti Microsoft.
- Zaregistrujte úložiště produktů.
- Nainstalujte požadované závislosti.

Stačí to provést jednou na jednom počítači.

Otevřete terminál a spusťte následující příkaz.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>Nainstalujte sadu .NET Core SDK.

Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte sadu .NET Core SDK. V terminálu spusťte následující příkaz.

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Instalace core runtime

Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte ASP.NET runtime. V terminálu spusťte následující příkaz.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalace runtime jádra .NET

Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte za běhu .NET Core. V terminálu spusťte následující příkaz.

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Poradce při potížích se správcem balíčků

Tato část obsahuje informace o běžných chybách, které se mohou stát při instalaci rozhraní .NET Core pomocí správce balíčků.

### <a name="failed-to-fetch"></a>Načtení se nezdařilo.

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
