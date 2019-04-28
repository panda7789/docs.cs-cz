---
title: Předpoklady pro .NET Core ve Windows
description: Informace v závislosti na vaší Windows potřebujete počítač pro vývoj a spouštění aplikací .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 2941721dfa4b87d4113e4f4b529845e47f3dc1b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646823"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Předpoklady pro .NET Core ve Windows

Tento článek popisuje podporované verze operačního systému, aby bylo možné spustit aplikace .NET Core ve Windows. Podporované verze operačního systému a závislostech, které následují platí na tři způsoby, jak vyvíjet aplikace .NET Core ve Windows:

* [Příkazový řádek](tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [Visual Studio Code](https://code.visualstudio.com/)

Také, pokud vyvíjíte ve Windows pomocí sady Visual Studio 2017, [požadavky sady Visual Studio 2017](#prerequisites-with-visual-studio-2017) část ve více podrobností o minimální verze podporované pro vývoj v .NET Core.

## <a name="net-core-supported-windows-versions"></a>.NET core podporované verze Windows

.NET core je podporována v následujících verzích:

* Windows 7 SP1
* Windows 8.1
* Windows 10 Anniversary Update (verze 1607) nebo novější verze
* Windows Server 2008 R2 SP1 (plnou instalaci systému Server nebo Server Core)
* Windows Server 2012 SP1 (plnou instalaci systému Server nebo Server Core)
* Windows Server 2012 R2 (úplná Server nebo Server Core)
* Windows Server 2016 nebo novější verze (plnou instalaci systému Server, Server Core nebo Nano Server)

## <a name="net-core-supported-operating-systems"></a>.NET core podporované operační systémy

Následující články obsahují úplný seznam operačních systémů nepodporuje .NET Core na verze:

* [.NET core 3.0 (Preview)](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

Odkazy ke stažení a další informace najdete v tématu [stáhne .NET](https://dotnet.microsoft.com/download) ke stažení nejnovější verze nebo [.NET stáhne archivu](https://dotnet.microsoft.com/download/archives#dotnet-core) pro starší verze.

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

## <a name="prerequisites-for-net-core-30-preview-3"></a>Předpoklady pro .NET Core 3.0 ve verzi Preview 3

.NET core 3.0 ve verzi Preview 3 má stejné požadavky jako v jiných verzích .NET Core. Ale pokud budete chtít použít Visual Studio k vytvoření aplikace .NET Core 3.0 projektů, je nutné použít [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Visual Studio 2019 může být nainstalovaná – souběžně s jinými verzemi nástroje Visual Studio bez konfliktu.

## <a name="prerequisites-with-visual-studio-2017"></a>Požadavky sady Visual Studio 2017
    
Můžete použít libovolný editor k vývoji aplikací .NET Core pomocí sady .NET Core SDK. Visual Studio 2017 poskytuje integrované vývojové prostředí pro aplikace .NET Core ve Windows.

Další informace o změnách v sadě Visual Studio 2017 v [poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Můžete vyvíjet aplikace .NET Core v sadě Visual Studio 2017 pomocí .NET Core 2.2 SDK:

 1. [Stáhněte a nainstalujte Visual Studio 2017 verze 15.9.0 nebo vyšší](/visualstudio/install/install-visual-studio) s **vývoj pro různé platformy .NET Core** úloh (v **další sady nástrojů** části) vybrané.

![Instalace – snímek obrazovky sady Visual Studio 2017 s vybranou úlohou "Vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-2017-workloads.jpg)

Po **vývoj pro různé platformy .NET Core** je nainstalovaná sada nástrojů, Visual Studio obvykle nainstaluje předchozí verzi .NET Core SDK.
Například Visual Studio 2017 15.9 používá .NET Core 2.1 SDK ve výchozím nastavení po instalaci zatížení.

Aktualizace sady Visual Studio pro použití sady .NET Core 2.2 SDK:

 1. Nainstalujte [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).

 1. Pokud chcete projekt pro použití nejnovější modul runtime .NET Core, jejich cíl změnit existující nebo nové projekty .NET Core na .NET Core 2.2 využitím následujících pokynů:

    * Na **projektu** nabídce zvolte **vlastnosti**.
    * V **Cílová architektura** nabídce pro výběr, nastavte hodnotu na **.NET Core 2.2**.

![Snímek obrazovky sady Visual Studio 2017 aplikace vlastnost projektu pomocí nabídky ".NET Core 2.2" target framework vybrané položky](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Jakmile budete mít nakonfigurované s .NET Core 2.2 SDK sady Visual Studio, můžete provést následující akce:

* Otevřete, sestavte a spusťte existující projekty .NET Core 1.x a 2.x.
* Změnit cílení projektů .NET Core 1.x a 2.x na .NET Core 2.2, sestavení a spusťte.
* Vytvořte nové projekty .NET Core 2.2.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Můžete vyvíjet aplikace .NET Core 1.x v sadě Visual Studio [stáhnout a nainstalovat sadu Visual Studio 2017](/visualstudio/install/install-visual-studio) s **"Vývoj pro různé platformy .NET Core"** úloh (v **další sady nástrojů**části) vybrané.

![Instalace – snímek obrazovky sady Visual Studio 2017 s vybranou úlohou "Vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> Je možné použít Visual Studio 2015 pro vývoj v .NET Core 1.x, ale nedoporučuje z následujících důvodů:
  > * Nástroje .NET Core je verze preview, což není podporováno.
  > * Projekty, které jsou založeny na project.json, který je zastaralý.
>
> Další informace o změnách formát projektu naleznete v tématu [podrobný přehled změn](./tools/cli-msbuild-architecture.md).

---

<a name="vs-mapping"></a>

> [!TIP]
> Pokud chcete ověřit vaši verzi sady Visual Studio:
>
> * Na **pomáhají** nabídce zvolte **o Microsoft Visual Studio**.
> * V **o Microsoft Visual Studio** dialogového okna, zkontrolujte číslo verze.
>   * Pro aplikace .NET Core 3.0 ve verzi Preview 3, Visual Studio 2019 verze 16,0 nebo vyšší.
>   * Pro aplikace .NET Core 2.2, Visual Studio 2017 verze 15.9 nebo vyšší.
>   * Pro aplikace .NET Core 2.1, Visual Studio 2017 verze 15.7 nebo novější.
>   * Pro aplikace .NET Core 1.x, Visual Studio 2017 verze 15,0 nebo vyšší.