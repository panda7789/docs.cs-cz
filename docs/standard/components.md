---
title: Součásti architektury technologie .NET
description: Popisuje architektonické součásti rozhraní .NET, jako je například standard .NET, implementace .NET, runtimes .NET a nástroje.
author: cartermp
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 027fdb4cec47550f88f6930a4bbdff4ab5cdfb36
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344168"
---
# <a name="net-architectural-components"></a>Součásti architektury technologie .NET

Aplikace .NET je vyvinuta pro a běží v jedné nebo více *implementacích rozhraní .NET*.  Implementace rozhraní .NET zahrnují rozhraní .NET Framework, .NET Core a Mono. Existuje specifikace rozhraní API společná pro všechny implementace rozhraní .NET, která se nazývá .NET Standard. Tento článek poskytuje stručný úvod do každého z těchto konceptů.

## <a name="net-standard"></a>.NET Standard

.NET Standard je sada rozhraní API, které jsou implementovány knihovnou základních tříd implementace .NET. Formálněji je specifikace rozhraní API .NET, které tvoří jednotnou sadu smluv, proti kterým kompilujete kód. Tyto smlouvy jsou implementovány v každé implementaci rozhraní .NET. To umožňuje přenositelnost mezi různými implementacemi rozhraní .NET, což efektivně umožňuje spuštění kódu všude.

.NET Standard je také [cílový rámec](glossary.md#target-framework). Pokud váš kód cílí na verzi standardu .NET, může být spuštěn na libovolné implementaci rozhraní .NET, která tuto verzi rozhraní .NET Standard podporuje.

Další informace o standardu .NET a o tom, jak na něj cílit, naleznete [v tématu .NET Standard](net-standard.md).

## <a name="net-implementations"></a>Implementace rozhraní .NET

Každá implementace rozhraní .NET obsahuje následující součásti:

- Jeden nebo více runtimes. Příklady: CLR pro rozhraní .NET Framework, CoreCLR a CoreRT pro .NET Core.
- Knihovna tříd, která implementuje standard .NET a může implementovat další rozhraní API. Příklady: .NET Framework Base Class Library, .NET Core Base Class Library.
- Volitelně jeden nebo více rozhraní aplikace. Příklady: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md)a Windows Presentation Foundation [(WPF)](../framework/wpf/index.md) jsou zahrnuty v rozhraní .NET Framework a .NET Core.
- Volitelně, vývojové nástroje. Některé vývojové nástroje jsou sdíleny mezi více implementací.

Existují čtyři primární implementace rozhraní .NET, které společnost Microsoft aktivně vyvíjí a udržuje: .NET Core, .NET Framework, Mono a UPW.

### <a name="net-core"></a>.NET Core

.NET Core je implementace napříč platformami rozhraní .NET a je navržena tak, aby zpracovávala úlohy serveru a cloudu ve velkém měřítku. Běží na Windows, macOS a Linux. Implementuje standard .NET, takže kód, který cílí na standard .NET, může být spuštěn na jádru .NET. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [Windows Forms](../framework/winforms/windows-forms-overview.md)a Windows Presentation [Foundation (WPF)](../framework/wpf/index.md) jsou spuštěny na rozhraní .NET Core.

Další informace o jádru .NET najdete v [příručce .NET Core Guide](../core/index.yml) a [výběr mezi rozhraním .NET Core a rozhraní .NET Framework pro serverové aplikace](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

Rozhraní .NET Framework je původní implementace rozhraní .NET, která existuje od roku 2002. Verze 4.5 a novější implementují standard .NET, takže kód, který cílí na rozhraní .NET Standard, může být spuštěn v těchto verzích rozhraní .NET Framework. Obsahuje další řešení API specifická pro systém Windows, například api pro vývoj plochy systému Windows s windows forms a WPF. Rozhraní .NET Framework je optimalizováno pro vytváření desktopových aplikací systému Windows.

Další informace o rozhraní .NET Framework naleznete v [Příručce k rozhraní .NET Framework](../framework/index.yml).

### <a name="mono"></a>Mono

Mono je implementace .NET, která se používá hlavně v případě, že je vyžadován malý runtime. Je to runtime, který pohání aplikace Xamarin na Android, macOS, iOS, tvOS a watchOS a je zaměřen především na malé rozměry. Mono také pohání hry postavené pomocí motoru Unity.

Podporuje všechny aktuálně publikované verze .NET Standard.

Mono historicky implementoval větší API rozhraní .NET Framework a emuloval některé z nejpopulárnějších schopností na Unixu. Někdy se používá ke spuštění aplikací .NET, které jsou závislé na těchto funkcích na Unixu.

Mono se obvykle používá s kompilátorem just-in-time, ale obsahuje také úplný statický kompilátor (kompilace dopředu času), který se používá na platformách, jako je iOS.

Další informace o mono, naleznete [v dokumentaci Mono](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Univerzální platforma Windows (UPW)

Upw je implementace rozhraní .NET, která se používá pro vytváření moderních aplikací systému Windows s podporou dotykového ovládání a softwaru pro Internet věcí (IoT). Je navržen tak, aby sjednocovat různé typy zařízení, které můžete chtít cílit, včetně počítačů, tabletů, telefonů, a dokonce i Xbox. Upwp poskytuje mnoho služeb, jako je například centralizované úložiště aplikací, spuštění prostředí (AppContainer) a sadu windows API pro použití namísto Win32 (WinRT). Aplikace lze psát v jazycích C++, C#, Visual Basic a JavaScript. Při použití jazyka C# a jazyka Visual Basic jsou rozhraní API .NET poskytována rozhraním .NET Core.

Další informace o programu UPW najdete [v tématu Úvod k univerzální platformě Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Runtimes rozhraní .NET

Runtime je prostředí spuštění spravovaného programu. Operační systém je součástí runtime prostředí, ale není součástí běhu .NET. Zde jsou některé příklady runtimes rozhraní .NET:

- Běžný jazyk Runtime (CLR) pro rozhraní .NET Framework
- Core Common Language Runtime (CoreCLR) pro .NET Core
- Nativní rozhraní .NET pro univerzální platformu Windows
- Běhonastavení Mono pro Xamarin.iOS, Xamarin.Android, Xamarin.Mac a mono desktop framework

## <a name="net-tooling-and-common-infrastructure"></a>Nástroje .NET a společná infrastruktura

Máte přístup k rozsáhlé sadě nástrojů a součástí infrastruktury, které pracují s každou implementací rozhraní .NET. Mezi tyto nástroje a součásti patří:

- Jazyky .NET a jejich kompilátory
- Systém projektu .NET (založený na *souborech .csproj*, *.vbproj*a *.fsproj)*
- [MSBuild](/visualstudio/msbuild/msbuild), modul sestavení používaný k vytváření projektů
- [NuGet](/nuget/), správce balíčků společnosti Microsoft pro rozhraní .NET
- Nástroje orchestrace sestavení s otevřeným zdrojovým kódem, například [CAKE](https://cakebuild.net/) a [FAKE](https://fake.build/)

## <a name="applicable-standards"></a>Platné normy

Specifikace jazyka C# a společné jazykové infrastruktury (CLI) jsou standardizovány prostřednictvím [Ecma&reg;International](https://www.ecma-international.org/). První vydání těchto norem byla zveřejněna společností Ecma v prosinci 2001.

Následné revize norem byly vypracovány pracovními skupinami TC49-TG2 (C#) a TC49-TG3 (CLI) v rámci Technického výboru pro programovací jazyky[(TC49)](https://www.ecma-international.org/memento/tc49.htm)a přijaty Valným shromážděním ECMA a následně ISO/IEC JTC 1 prostřednictvím zrychleného procesu ISO.

### <a name="latest-standards"></a>Nejnovější standardy

Následující oficiální ecma dokumenty jsou k dispozici pro [C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm) a [CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) ([TR-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)):

- **C# Language Standard (verze 5.0)**: [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **Společná jazyková infrastruktura**: K dispozici ve [formátu pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) a [ve formě zip.](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip)
- **Informace odvozené ze souboru XML oddílu IV**: K dispozici ve formátu [pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) a [zip.](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip)

Oficiální dokumenty ISO/IEC jsou k dispozici na stránce ISO/IEC [Publicly Available Standards.](https://standards.iso.org/ittf/PubliclyAvailableStandards/) Tyto odkazy jsou přímo z této stránky:

- **Informační technologie - Programovací jazyky - C#**: [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **Informační technologie – Oddíly I až VI společné jazykové infrastruktury**( I až VI : [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **Informační technologie – Společná jazyková infrastruktura (CLI) – Technická zpráva o informacích odvozených ze souboru XML oddílu IV**: [ISO/IEC TR 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>Viz také

- [Volba mezi .NET Core a .NET Framework pro serverové aplikace](choosing-core-framework-server.md)
- [.NET Standard](net-standard.md)
- [Základní příručka rozhraní .NET](../core/index.yml)
- [Průvodce rámcem rozhraní .NET](../framework/index.yml)
- [Průvodce C#](../csharp/index.yml)
- [Průvodce F#](../fsharp/index.yml)
- [Průvodce visual basicem](../visual-basic/index.yml)
