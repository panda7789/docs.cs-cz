---
title: Instalace .NET Core na SLES 15 - správce balíčků - .NET Core
description: Pomocí správce balíčků nainstalujte na sles 15 .NET Core SDK a runtime.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b86b97bf17165f2f7a70e80ff581750ba39be375
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134179"
---
# <a name="sles-15-package-manager---install-net-core"></a>SLES 15 Správce balíčků - instalace jádra .NET

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na SLES 15.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a>Registrace klíče Microsoft a informačního kanálu

Před instalací rozhraní .NET budete muset:

- Zaregistrujte klíč Společnosti Microsoft.
- Zaregistrujte úložiště produktů.
- Nainstalujte požadované závislosti.

Stačí to provést jednou na jednom počítači.

Otevřete terminál a spusťte následující příkaz.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
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

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]
