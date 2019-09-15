---
title: Předpoklady pro .NET Core ve Windows
description: Zjistěte, jaké závislosti potřebujete na počítači s Windows pro vývoj a spouštění aplikací .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 7b2bf2b8353c4f02fa11e9e7531e0d936007be0b
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970286"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Předpoklady pro .NET Core ve Windows

Tento článek ukazuje podporované verze operačního systému, aby bylo možné spouštět aplikace .NET Core ve Windows. Podporované verze operačního systému a závislosti, které následují, se vztahují na tři způsoby vývoje aplikací .NET Core v systému Windows:

* [Příkazový řádek](tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [Visual Studio Code](https://code.visualstudio.com/)

Pokud vyvíjíte v systému Windows pomocí sady Visual Studio 2017, v části [požadavky se sadou Visual studio 2017](#prerequisites-with-visual-studio-2017) podrobnější informace o minimálních verzích podporovaných pro vývoj pro .NET Core.

## <a name="net-core-supported-operating-systems"></a>Podporované operační systémy .NET Core

Následující články obsahují úplný seznam podporovaných operačních systémů .NET Core na verzi:

* [.NET Core 3,0 (Preview)](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET Core 1,0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

Odkazy ke stažení a další informace najdete v tématu stažení z [rozhraní .NET](https://dotnet.microsoft.com/download) pro stažení nejnovější verze nebo [archivu ke stažení](https://dotnet.microsoft.com/download/archives#dotnet-core) pro starší verze.

## <a name="net-core-dependencies"></a>Závislosti .NET Core

.NET Core 1,1 a starší verze vyžadují při spuštění C++ ve verzích Windows starších než Windows 10 a windows Server 2016 vizuál Redistributable. Tato závislost je automaticky nainstalována instalačním programem .NET Core.

[Distribuovatelné C++ součásti Microsoft Visual 2015 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) je třeba nainstalovat ručně v těchto případech:

* Instalace .NET Core pomocí [skriptu instalačního programu](./tools/dotnet-install-script.md).
* Nasazení samostatně obsažené aplikace .NET Core.
* Sestavuje se produkt ze zdroje.
* Instalace .NET Core přes soubor *. zip* . To může zahrnovat servery sestavení/CI/CD.

> [!NOTE]
> **Pro Windows 8.1 a starší verze nebo Windows Server 2012 R2 a starší verze:**
>
> Ujistěte se, že je instalace Windows aktuální a zahrnuje [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), která se dá nainstalovat prostřednictvím web Windows Update. Pokud tuto aktualizaci nemáte nainstalovanou, při spuštění aplikace .NET Core se zobrazí chybová zpráva podobná následující:`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Pro Windows 7 nebo Windows Server 2008 R2:**
>
> Kromě KB2999226 se ujistěte, že máte nainstalovanou také [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) . Pokud tuto aktualizaci nemáte nainstalovanou, při spuštění aplikace .NET Core se zobrazí chybová zpráva podobná následující: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-for-net-core-30-preview-3"></a>Předpoklady pro .NET Core 3,0 Preview 3

.NET Core 3,0 Preview 3 má stejné požadavky jako jiné verze .NET Core. Pokud však chcete použít aplikaci Visual Studio k vytvoření projektu .NET Core 3,0, je nutné použít [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Sadu Visual Studio 2019 lze nainstalovat souběžně s jinými verzemi sady Visual Studio bez konfliktu.

## <a name="prerequisites-with-visual-studio-2017"></a>Požadavky v rámci sady Visual Studio 2017
    
K vývoji aplikací .NET Core pomocí .NET Core SDK můžete použít libovolný editor. Visual Studio 2017 poskytuje integrované vývojové prostředí pro aplikace .NET Core ve Windows.

V poznámkách k [verzi](/visualstudio/releasenotes/vs2017-relnotes)si můžete přečíst další informace o změnách v aplikaci Visual Studio 2017.

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Vývoj aplikací .NET Core v sadě Visual Studio 2017 pomocí sady .NET Core 2,2 SDK:

 1. [Stáhněte a nainstalujte si sadu Visual Studio 2017 verze 15.9.0 nebo novější](/visualstudio/install/install-visual-studio) pomocí úlohy **vývoje .NET Core pro různé platformy** (v části **jiné sady nástrojů** ).

![Snímek obrazovky s instalací sady Visual Studio 2017 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-2017-workloads.jpg)

Po instalaci sady nástrojů pro **vývoj pro různé platformy .NET Core** se v sadě Visual Studio obvykle nainstaluje předchozí verze .NET Core SDK.
Sada Visual Studio 2017 15,9 například po instalaci úlohy používá .NET Core 2,1 SDK ve výchozím nastavení.

Aktualizace sady Visual Studio tak, aby používala sadu .NET Core 2,2 SDK:

 1. Nainstalujte [sadu .NET Core 2,2 SDK](https://dotnet.microsoft.com/download).

 1. Pokud chcete, aby váš projekt používal nejnovější modul runtime .NET Core, přecílíte stávající nebo nové projekty .NET Core na .NET Core 2,2 pomocí následujících pokynů:

    * V nabídce **projekt** klikněte na příkaz **vlastnosti**.
    * V nabídce Výběr **cílového rozhraní** nastavte hodnotu na **.NET Core 2,2**.

![Snímek vlastnosti projektu aplikace sady Visual Studio 2017 s vybranou položkou nabídky cílové rozhraní .NET Core 2,2](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Jakmile máte sadu Visual Studio nakonfigurovanou pomocí sady .NET Core 2,2 SDK, můžete provést následující akce:

* Otevřete, sestavte a spusťte existující projekty .NET Core 1. x a 2. x.
* Proveďte změny cílení na projekty .NET Core 1. x a 2. x na .NET Core 2,2, sestavte a spusťte.
* Vytvořte nové projekty .NET Core 2,2.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Pro vývoj aplikací .NET Core 1. x v sadě Visual Studio [Stáhněte a nainstalujte sadu Visual Studio 2017](/visualstudio/install/install-visual-studio) s úlohou **"vývoj pro různé sady nástrojů .NET Core"** (v části **ostatní sady nástrojů** ).

![Snímek obrazovky s instalací sady Visual Studio 2017 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> Je možné použít Visual Studio 2015 pro vývoj pro .NET Core 1. x, ale nedoporučuje se z následujících důvodů:
>
> * Nástroje .NET Core jsou verze Preview, což není podporováno.
> * Projekty jsou založené na projektu Project. JSON, který je zastaralý.
>
> Další informace o změnách formátu projektu naleznete v části [Přehled změn na nejvyšší úrovni](./tools/cli-msbuild-architecture.md).

---

<a name="vs-mapping"></a>

> [!TIP]
> Ověření verze sady Visual Studio:
>
> * V nabídce **help (nápovědu** ) vyberte **informace o Microsoft Visual Studio**.
> * V dialogovém okně **o Microsoft Visual Studio** ověřte číslo verze.
>   * Pro aplikace .NET Core 3,0 Preview 3, Visual Studio 2019 verze 16,0 nebo vyšší.
>   * Pro aplikace .NET Core 2,2, Visual Studio 2017 verze 15,9 nebo vyšší.
>   * Pro aplikace .NET Core 2,1, Visual Studio 2017 verze 15,7 nebo vyšší.
>   * Pro aplikace .NET Core 1. x, Visual Studio 2017 verze 15,0 nebo vyšší.
