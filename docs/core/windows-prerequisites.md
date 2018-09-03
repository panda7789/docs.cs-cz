---
title: Předpoklady pro .NET Core ve Windows
description: Informace v závislosti na vaší Windows potřebujete počítač pro vývoj a spouštění aplikací .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 08/31/2018
ms.openlocfilehash: bbf54c8d215783656830f0fa035708be82a7c39c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482607"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Předpoklady pro .NET Core ve Windows

Tento článek popisuje závislosti, které potřebujete pro vývoj aplikací .NET Core ve Windows. Podporované verze operačního systému a závislostech, které následují platí na tři způsoby, jak vyvíjet aplikace .NET Core ve Windows:

* [Příkazový řádek](tutorials/using-with-xplat-cli.md)
* [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a>.NET core podporované verze Windows

.NET core je podporována v následujících verzích:

* Windows 7 SP1
* Windows 8.1
* Windows 10 Anniversary Update (verze 1607) nebo novější verze
* Windows Server 2008 R2 SP1 (plnou instalaci systému Server nebo Server Core)
* Windows Server 2012 SP1 (plnou instalaci systému Server nebo Server Core)
* Windows Server 2012 R2 (úplná Server nebo Server Core)
* Windows Server 2016 nebo novější verze (plnou instalaci systému Server, Server Core nebo Nano Server)

Následující články obsahují úplný seznam operačních systémů nepodporuje .NET Core na verze:

* [.NET core 2.1 – podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET core 2.0 – podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [.NET core 1.x – verze podporovaný operační systém](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a>.NET core závislosti

Při spuštění na verzích Windows starších než Windows 10 a Windows serveru 2016 vyžadují Visual C++ Redistributable .NET core 1.1 a staršími verzemi. Tato závislost je automaticky nainstalován pomocí instalačního programu .NET Core.

[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musí ručně doinstalovat při:

* Instalace .NET Core s [skript instalačního programu](./tools/dotnet-install-script.md).
* Nasazení samostatné aplikaci .NET Core.
* Sestavení produktu ze zdroje.
* Instalace .NET Core prostřednictvím *ZIP* souboru. To může zahrnovat servery sestavení/CI/CD.

> [!NOTE]
> **Pro Windows 8.1 a starší verze, nebo Windows Server 2012 R2 a dřívějších verzích:**
>
> Ujistěte se, že instalace systému Windows je aktuální a zahrnuje [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), kterou je možné nainstalovat prostřednictvím služby Windows Update. Pokud nemáte k dispozici tato aktualizace instalována, zobrazí se vám chyba následujícím postupem při spuštění aplikace rozhraní .NET Core: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Pro Windows 7 nebo Windows Server 2008 R2:**
>
> Kromě KB2999226, ujistěte se, že budete mít taky [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) nainstalované. Pokud nemáte k dispozici tato aktualizace instalována, zobrazí se zpráva podobná následující při spuštění aplikace rozhraní .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-with-visual-studio-2017"></a>Požadavky sady Visual Studio 2017

Můžete použít libovolný editor k vývoji aplikací .NET Core pomocí sady .NET Core SDK. [Visual Studio 2017](#visual-studio-2017) poskytuje integrované vývojové prostředí pro aplikace .NET Core ve Windows.

Další informace o změnách v sadě Visual Studio 2017 v [poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

Můžete vyvíjet aplikace .NET Core 2.1 v sadě Visual Studio 2017:

 1. [Stažení a instalace sady Visual Studio 2017 verze 15.7.0 nebo vyšší](/visualstudio/install/install-visual-studio) s **vývoj pro různé platformy .NET Core** úloh (v **další sady nástrojů** části) vybrané.

![Instalace – snímek obrazovky sady Visual Studio 2017 s vybranou úlohou "Vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-15-8-workloads.jpg)

Po **vývoj pro různé platformy .NET Core** sada nástrojů je ve výchozím nastavení nainstalované, Visual Studio 2017 15.7 používá .NET Core 2.0 SDK a Visual Studio 2017 15.8 používá sadu SDK 2.1.

 2. Pokud používáte Visual Studio 2017 15.7, nainstalujte [sady SDK .NET Core 2.1](https://www.microsoft.com/net/download/core) nebo upgrade na Visual Studio 2017 15.8.

 3. Změnit cíl existující nebo nové projekty .NET Core na .NET Core 2.1 pomocí následujících pokynů:
    * Na **projektu** nabídce zvolit **vlastnosti**.
    * V **Cílová architektura** nabídce pro výběr, nastavte hodnotu na **.NET Core 2.1**.

![Snímek obrazovky sady Visual Studio 2017 aplikace vlastnost projektu pomocí nabídky ".NET Core 2.0" Target framework vybrané položky](./media/windows-prerequisites/Targeting-dotnetCore2.png)

Jakmile budete mít nakonfigurované pomocí sady SDK .NET Core 2.1 sady Visual Studio, můžete provést následující akce:

* Otevřete, sestavte a spusťte existující projekty .NET Core 1.x a 2.x.
* Změnit cíl .NET Core 1.x a 2.0 projekty .NET Core 2.1, sestavit a spustit.
* Vytvořte nové projekty .NET Core 2.1.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

Můžete vyvíjet aplikace .NET Core 2.0 v sadě Visual Studio 2017:

 1. [Stáhněte a nainstalujte Visual Studio 2017 verze 15.3.0 nebo vyšší](/visualstudio/install/install-visual-studio) s **vývoj pro různé platformy .NET Core** úloh (v **další sady nástrojů** části) vybrané.

![Instalace – snímek obrazovky sady Visual Studio 2017 s vybranou úlohou "Vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-15-3-workloads.jpg)

Po **vývoj pro různé platformy .NET Core** je nainstalovaná sada nástrojů, Visual Studio 2017 používá .NET Core 1.x ve výchozím nastavení. Instalace .NET Core 2.0 SDK potřebujete podporu .NET Core 2.0 v sadě Visual Studio 2017.

 2. Nainstalujte [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/dotnet-core/2.0).
 3. Změnit cíl stávajícího nebo nového .NET Core 1.x projekty .NET Core 2.0 pomocí následujících pokynů:
    * Na **projektu** nabídce zvolit **vlastnosti**.
    * V **Cílová architektura** nabídce pro výběr, nastavte hodnotu na **.NET Core 2.0**.

![Snímek obrazovky sady Visual Studio 2017 aplikace vlastnost projektu pomocí nabídky ".NET Core 2.0" Target framework vybrané položky](./media/windows-prerequisites/Targeting-dotnetCore2.png)

Po instalaci rozhraní .NET Core 2.0 SDK je Visual Studio 2017 ve výchozím nastavení používá rozhraní .NET Core SDK 2.0 a podporuje následující akce:

* Otevřete, sestavte a spusťte existující projekty .NET Core 1.x.
* Změnit cíl projektů .NET Core 1.x do .NET Core 2.0, sestavení a spusťte.
* Vytvořte nové projekty .NET Core 2.0.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

Můžete vyvíjet aplikace .NET Core 1.x v sadě Visual Studio [stáhnout a nainstalovat sadu Visual Studio 2017](/visualstudio/install/install-visual-studio) s **"Vývoj pro různé platformy .NET Core"** úloh (v **další sady nástrojů**části) vybrané.

![Instalace – snímek obrazovky sady Visual Studio 2017 s vybranou úlohou "Vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> Je možné použít Visual Studio 2015 pro vývoj v .NET Core 1.x, ale nedoporučuje z následujících důvodů:
  > * Nástroje .NET Core je verze preview, což není podporováno.
  > * Projekty, které jsou založeny na project.json, který je zastaralý.
>
> Další informace o změnách formát projektu naleznete v tématu [podrobný přehled změn](./tools/cli-msbuild-architecture.md).
---

<a name="vs-mapping"></a>

> [!TIP]
> Pokud chcete ověřit vaši verzi sady Visual Studio 2017:
>
> * Na **pomáhají** nabídce zvolte **o Microsoft Visual Studio**.
> * V **o Microsoft Visual Studio** dialogového okna, zkontrolujte číslo verze.
>   * Pro aplikace .NET Core 2.2 ve verzi Preview 1, Visual Studio 2017 (aktuálně ve verzi Preview) verzi 15.9 nebo vyšší.
>   * Pro aplikace .NET Core 2.1, Visual Studio 2017 verze 15.7 nebo novější.
>   * Pro aplikace .NET Core 2.0, Visual Studio 2017 verze 15.3 nebo novější.
>   * Pro aplikace .NET Core 1.x, Visual Studio 2017 verze 15,0 nebo vyšší.
