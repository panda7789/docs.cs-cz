---
title: Předpoklady pro .NET Core na Macu
description: Podporované verze macOS a závislosti rozhraní .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na macOS počítačích.
author: thraka
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 10/11/2019
ms.openlocfilehash: 2d4fc0b37be08988440325db8b507124c36bf053
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318314"
---
# <a name="prerequisites-for-net-core-on-macos"></a>Předpoklady pro .NET Core v macOS

V tomto článku se dozvíte o podporovaných verzích macOS a závislostech .NET Core, které potřebujete k vývoji, nasazování a spouštění aplikací .NET Core na počítačích s macOS. Podporované verze operačního systému a závislosti, které následují, se vztahují na tři způsoby vývoje aplikací .NET Core na Macu: prostřednictvím [příkazového řádku s oblíbeným editorem](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)a [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

## <a name="downloads-and-dependencies"></a>Soubory ke stažení a závislosti

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3,0 se podporuje na **MacOS vysokých Sierra (verze 10,13)** a novějších verzích. Je vyžadována architektura procesoru **x64** .

Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0) . [Podporované verze operačního systému .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pro úplný seznam podporovaných operačních systémů pro .net Core 3,0, distribucí a verzí, nepodporovaných verzí operačního systému a propojení zásad životního cyklu.

Seznam známých problémů najdete v tématu [známé problémy .NET Core](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

.NET Core 2,2 se podporuje na **MacOS Sierra (verze 10,12)** a novějších verzích. Je vyžadována architektura procesoru **x64** .

Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) . [Podporované verze operačního systému .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) pro úplný seznam podporovaných operačních systémů pro .net Core 2,2, distribucí a verzí, nepodporovaných verzí operačního systému a propojení zásad životního cyklu.

Seznam známých problémů najdete v tématu [známé problémy .NET Core](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

.NET Core 2,1 se podporuje na **MacOS Sierra (verze 10,12)** a novějších verzích. Je vyžadována architektura procesoru **x64** .

Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) . [Podporované verze operačního systému .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) pro úplný seznam podporovaných operačních systémů pro .net Core 2,1, distribucí a verzí, nepodporovaných verzí operačního systému a propojení zásad životního cyklu.

Seznam známých problémů najdete v tématu [známé problémy .NET Core](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).

---

## <a name="libgdiplus"></a>libgdiplus

Aplikace .NET Core, které používají *System. Drawing. Common* Assembly, vyžadují, aby bylo možné nainstalovat libgdiplus.

Snadný způsob, jak získat libgdiplus, je použít Správce balíčků [homebrew ("Brew")](https://brew.sh/) pro MacOS. Po instalaci *Brew*nainstalujte libgdiplus spuštěním následujících příkazů na příkazovém řádku terminálu (Command):

```console
brew update
brew install libgdiplus
```

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

K vývoji aplikací .NET Core pomocí .NET Core SDK můžete použít libovolný editor. Pokud ale chcete vyvíjet aplikace .NET Core na Macu v integrovaném vývojovém prostředí, můžete použít [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).
