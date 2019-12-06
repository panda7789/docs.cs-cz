---
title: Instalace .NET Core na Ubuntu 19,04 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v Ubuntu 19,04.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 98ceb0ae7f3fbd99c4be412fd1e19928793c348f
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836890"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a>Správce balíčků Ubuntu 19,04 – instalace .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Ubuntu 19,04. Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.

## <a name="register-microsoft-key-and-feed"></a>Registrace klíče Microsoft a informačního kanálu

Před instalací .NET budete potřebovat:

- Registrace klíče Microsoftu
- registrace úložiště produktu
- Nainstalovat požadované závislosti

Stačí to provést jednou na jednom počítači.

Otevřete terminál a spusťte následující příkazy.

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>Instalace .NET Core SDK

Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK. V terminálu spusťte následující příkazy.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> Pokud se zobrazí chybová zpráva podobná této chybě **nelze nalézt balíček dotnet-SDK-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .

## <a name="install-the-aspnet-core-runtime"></a>Instalace modulu runtime ASP.NET Core

Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte modul runtime ASP.NET Core. V terminálu spusťte následující příkazy.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Pokud se zobrazí chybová zpráva podobná té, že **nejde najít Package aspnetcore-runtime-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .

## <a name="install-the-net-core-runtime"></a>Instalace modulu runtime .NET Core

Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core. V terminálu spusťte následující příkazy.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> Pokud se zobrazí chybová zpráva podobná řetězci **nelze nalézt balíček dotnet-runtime-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Řešení potíží se správcem balíčků

Pokud se zobrazí chybová zpráva podobná té, že se **nepovedlo najít balíček {Package .NET Core}** , spusťte následující příkazy.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Pokud to nefunguje, můžete spustit ruční instalaci pomocí následujících příkazů.

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```
