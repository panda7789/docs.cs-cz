---
title: Instalace .NET Core na openSUSE 15 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v openSUSE 15.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: cba07bafc32cc71a1cdaec08902284e105af4776
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740667"
---
# <a name="opensuse-15-package-manager---install-net-core"></a>Správce balíčků openSUSE 15 – instalace .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na openSUSE 15. Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.

## <a name="register-microsoft-key-and-feed"></a>Registrace klíče Microsoft a informačního kanálu

Před instalací .NET budete potřebovat:

- Zaregistrujte si klíč Microsoft.
- Zaregistrujte úložiště produktu.
- Nainstalujte požadované závislosti.

Stačí to provést jednou na jednom počítači.

Otevřete terminál a spusťte následující příkazy.

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="dependency-error-with-net-core-31"></a>Chyba závislosti s .NET Core 3,1

Informační kanál balíčku .NET Core 3,1 pro openSUSE má problém se závislostí **krb5** . Před instalací .NET Core 3,1 nebo ASP.NET Core 3,1 nainstalujte správné závislosti pomocí následujícího příkazu.

```bash
sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
```

## <a name="install-the-net-core-sdk"></a>Instalace .NET Core SDK

Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK. V terminálu spusťte následující příkaz.

```bash
sudo zypper install dotnet-sdk-3.1
```

> [!IMPORTANT]
> Informační kanál balíčku .NET Core 3,1 pro openSUSE má problém se závislostí **krb5** . Pomocí následujícího příkazu nainstalujte správné závislosti a pak nainstalujte sadu .NET Core 3,1 SDK.
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-aspnet-core-runtime"></a>Instalace modulu runtime ASP.NET Core

Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET. V terminálu spusťte následující příkaz.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Informační kanál balíčku .NET Core 3,1 pro openSUSE má problém se závislostí **krb5** . Pomocí následujícího příkazu nainstalujte správné závislosti a pak nainstalujte modul runtime ASP.NET Core 3,1.
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-net-core-runtime"></a>Instalace modulu runtime .NET Core

Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core. V terminálu spusťte následující příkaz.

```bash
sudo zypper install dotnet-runtime-3.1
```

> [!IMPORTANT]
> Informační kanál balíčku .NET Core 3,1 pro openSUSE má problém se závislostí **krb5** . Pomocí následujícího příkazu nainstalujte správné závislosti a pak nainstalujte modul runtime .NET Core 3,1.
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
