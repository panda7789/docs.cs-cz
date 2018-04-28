---
title: Předpoklady pro .NET Core v systému Windows
description: Zjistěte, co závislosti, musíte na váš Windows počítače pro vývoj a spouštění aplikací .NET Core.
author: JRAlexander
ms.author: johalex
ms.date: 04/24/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 6f2ba8540a38f8e30d3d968f5e2c891c850053aa
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a>Předpoklady pro .NET Core v systému Windows

Tento článek ukazuje závislosti potřebné k vývoji aplikací .NET Core v systému Windows. Podporované verze operačního systému a závislosti, které platí na tři způsoby, jak vývoj aplikací .NET Core v systému Windows:

* [Příkazový řádek](tutorials/using-with-xplat-cli.md)
* [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a>.NET core podporované verze systému Windows

.NET core je podporována v následujících verzích:

* Windows 7 SP1
* Windows 8.1
* Windows 10 Anniversary Update (verze 1607) nebo novější verze
* Windows Server 2008 R2 SP1 (celého serveru nebo jádra serveru)
* Windows Server 2012 SP1 (celého serveru nebo jádra serveru)
* Windows Server 2012 R2 (celého serveru nebo jádra serveru)
* Windows Server 2016 (celý Server, Server Core nebo Nano Server)

V tématu [.NET Core 2.x – podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy.

V tématu [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy.

## <a name="net-core-dependencies"></a>.NET core závislosti

.NET core 1.1 a starší verze vyžadují Visual C++ Redistributable při spuštění na verzích Windows starších než Windows 10 a Windows Server 2016. Tuto závislost automaticky instalovaný s verzí instalačního programu .NET Core.

[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musí ručně nainstalovat při:

* Instalaci .NET Core s [skript instalačního programu](./tools/dotnet-install-script.md).
* Nasazení nezávislý aplikace .NET Core.
* Vytváření produktu ze zdroje.
* Instalaci .NET Core prostřednictvím *.zip* souboru. To může zahrnovat servery sestavení nebo položek konfigurace nebo disku CD.

> [!NOTE]
> *Windows 8.1 a starší verze, nebo Windows Server 2012 R2 a starších verzích:* Ujistěte se, že je aktuální instalace systému Windows a zahrnuje [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) který lze nainstalovat pomocí služby Windows Update. Pokud nemáte k dispozici tato aktualizace instalována, zobrazí chybu při spuštění aplikace .NET Core takto: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`.

## <a name="prerequisites-with-visual-studio-2017"></a>Požadavky s Visual Studio 2017

K vývoji aplikací .NET Core pomocí sady .NET Core SDK můžete použít všechny editor. [Visual Studio 2017](#visual-studio-2017) poskytuje integrované vývojové prostředí pro aplikace .NET Core v systému Windows.

Další informace o změnách ve Visual Studio 2017 v [poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

K vývoji aplikací .NET Core 2.x ve Visual Studio 2017:

 1. [Stáhněte a nainstalujte Visual Studio 2017 verze 15.3.0 nebo vyšší](/visualstudio/install/install-visual-studio) s **vývoj pro různé platformy .NET Core** zatížení (v **ostatní modulové** část) vybrané.

![Snímek obrazovky nástroje Visual Studio 2017 instalace se zatížením "Vývoj pro různé platformy .NET Core" vybrali](./media/windows-prerequisites/vs-15-3-workloads.jpg)

Po **vývoj pro různé platformy .NET Core** je nainstalovaná sada nástrojů, Visual Studio 2017 používá .NET Core 1.x ve výchozím nastavení. Instalace .NET Core 2.x SDK získat podporu 2.x .NET Core v Visual Studio 2017.

 2. Nainstalujte [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).
 3. Změňte cíl existující nebo nové projekty 1.x .NET Core na .NET Core 2.x pomocí následujících pokynů:
    * Na **projektu** nabídce zvolte **vlastnosti**.
    * V **cílové rozhraní** výběr nabídky, nastavte hodnotu na **.NET Core 2.0**.

![Snímek obrazovky nástroje Visual Studio 2017 aplikace projektu vlastnost s nabídky ".NET Core 2.0" Target framework vybrané položce](./media/windows-prerequisites/Targeting-dotnetCore2.png)

Jednou .NET Core 2.x SDK je nainstalovaná, Visual Studio 2017 používá rozhraní .NET Core SDK 2.x ve výchozím nastavení a podporuje následující akce:

* Otevřete, sestavte a spusťte existující projekty 1.x .NET Core.
* Změňte cíl .NET Core 1.x projekty 2.x, sestavení a spuštění .NET Core.
* Vytvořte nové projekty 2.x .NET Core.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

Vývoj aplikací .NET Core 1.x v sadě Visual Studio, [stáhněte a nainstalujte Visual Studio 2017 RTM (verze 15.0.26228.4) nebo vyšší](/visualstudio/install/install-visual-studio) s **"Vývoj pro různé platformy .NET Core"** zatížení (v  **Ostatní modulové** část) vybrané.

![Snímek obrazovky nástroje Visual Studio 2017 instalace se zatížením "Vývoj pro různé platformy .NET Core" vybrali](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> Je možné použít Visual Studio 2015 pro vývoj 1.x .NET Core, ale nedoporučuje z následujících důvodů:
  > * Nástrojů .NET Core je ve verzi preview, což není podporováno.
  > * Projekty jsou založené na souboru project.json, který je zastaralý.
>
> Další informace o změnách formátu projektu najdete v tématu [přehled změn](./tools/cli-msbuild-architecture.md).
---

> [!TIP]
> Chcete-li ověřit vaši verzi Visual Studio 2017:
>
> * Na **pomoci** nabídce zvolte **o sadě Microsoft Visual Studio**.
> * V **o sadě Microsoft Visual Studio** dialogové okno, zkontrolujte číslo verze.
>   * Pro aplikace .NET Core 2.1 Preview 1, Visual Studio 2017 15,6 operací verze Preview 6 nebo vyšší.
>   * Pro aplikace .NET Core 2.0, Visual Studio 2017 verze 15.3 nebo vyšší.
>   * Pro aplikace .NET Core 1.x, Visual Studio 2017 verze 15,0 nebo vyšší.
