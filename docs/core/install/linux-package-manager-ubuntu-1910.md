---
title: Instalace rozhraní .NET Core na správce balíčků Ubuntu 19.10 - .NET Core
description: Pomocí správce balíčků nainstalujte do Ubuntu 19.10 .NET Core SDK a runtime.
author: thraka
ms.author: adegeo
ms.date: 01/16/2020
ms.openlocfilehash: b8fec2afa6f03e3dabbf1ff449431759087163ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920653"
---
# <a name="ubuntu-1910-package-manager---install-net-core"></a>Ubuntu 19.10 Správce balíčků - Instalace .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na Ubuntu 19.10. Pokud instalujete runtime, doporučujeme nainstalovat [ASP.NET core runtime](#install-the-aspnet-core-runtime), protože zahrnuje rozhraní .NET Core i ASP.NET Core runtime.

## <a name="register-microsoft-key-and-feed"></a>Registrace klíče Microsoft a informačního kanálu

Před instalací rozhraní .NET budete muset:

- Zaregistrujte klíč Společnosti Microsoft.
- Zaregistrujte úložiště produktů.
- Nainstalujte požadované závislosti.

Stačí to provést jednou na jednom počítači.

Otevřete terminál a spusťte následující příkazy.

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>Nainstalujte sadu .NET Core SDK.

Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte sadu .NET Core SDK. V terminálu spusťte následující příkazy.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> Pokud se zobrazí chybová zpráva podobná **možnosti Nelze vyhledat balíček dotnet-sdk-3.1**, [přečtěte si část Poradce při potížích se správcem balíčků.](#troubleshoot-the-package-manager)

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Instalace core runtime

Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte ASP.NET core runtime. V terminálu spusťte následující příkazy.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Pokud se zobrazí chybová zpráva podobná **nelze najít balíček aspnetcore-runtime-3.1**, naleznete [v části Poradce při potížích s správcem balíčků.](#troubleshoot-the-package-manager)

## <a name="install-the-net-core-runtime"></a>Instalace runtime jádra .NET

Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte za běhu .NET Core. V terminálu spusťte následující příkazy.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> Pokud se zobrazí chybová zpráva podobná **nelze najít balíček dotnet-runtime-3.1**, naleznete [v části Poradce při potížích s správcem balíčků.](#troubleshoot-the-package-manager)

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Poradce při potížích se správcem balíčků

Tato část obsahuje informace o běžných chybách, které se mohou stát při instalaci rozhraní .NET Core pomocí správce balíčků.

### <a name="unable-to-locate"></a>Nelze najít

Pokud se zobrazí chybová zpráva podobná **příkazu Nelze najít balíček {balíček .NET Core}**, spusťte následující příkazy.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Pokud to nepomůže, můžete spustit ruční instalaci pomocí následujících příkazů.

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>Načtení se nezdařilo.

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
