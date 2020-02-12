---
title: Komponenty architektury .NET
description: Popisuje součásti architektury .NET, jako jsou .NET Standard, implementace .NET, moduly runtime .NET a nástroje.
author: cartermp
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: af28863ac98ff5ffb5a8133fb98f2f1e7036985d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124387"
---
# <a name="net-architectural-components"></a>Komponenty architektury .NET

Aplikace .NET je vyvíjena pro a spuštěna v rámci jedné nebo více *implementací rozhraní .NET*.  Implementace rozhraní .NET zahrnují .NET Framework, .NET Core a mono. Specifikace rozhraní API je společná pro všechny implementace .NET, které se nazývají .NET Standard. Tento článek obsahuje stručný úvod ke každé z těchto konceptů.

## <a name="net-standard"></a>.NET Standard

.NET Standard je sada rozhraní API, která jsou implementována základní knihovnou tříd implementace rozhraní .NET. V tomto případě je to specifikace rozhraní .NET API, které tvoří jednotnou sadu kontraktů, se kterými kompilujete kód. Tyto smlouvy jsou implementovány v každé implementaci rozhraní .NET. To umožňuje přenositelnost napříč různými implementacemi rozhraní .NET a efektivně umožňuje, aby váš kód běžel všude.

.NET Standard je také [cílovou architekturou](glossary.md#target-framework). Pokud váš kód cílí na verzi .NET Standard, může běžet v jakékoli implementaci rozhraní .NET, která podporuje tuto verzi .NET Standard.

Další informace o .NET Standard a o tom, jak je cílit, najdete v tématu [.NET Standard](net-standard.md) .

## <a name="net-implementations"></a>Implementace rozhraní .NET

Každá implementace rozhraní .NET zahrnuje tyto komponenty:

- Jeden nebo více modulů runtime. Příklady: CLR pro .NET Framework, CoreCLR a CoreRT pro .NET Core.
- Knihovna tříd, která implementuje .NET Standard a může implementovat další rozhraní API. Příklady: .NET Framework základní knihovny tříd, knihovna základních tříd .NET Core.
- Volitelně jeden nebo více aplikačních architektur. Příklady: [ASP.NET](https://www.asp.net/), [model Windows Forms](../framework/winforms/windows-forms-overview.md)a [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) jsou součástí .NET Framework a .NET Core.
- Volitelně vývojové nástroje. Některé vývojové nástroje se sdílejí mezi více implementacemi.

Společnost Microsoft aktivně vyvíjí a udržuje čtyři implementace v rozhraní .NET: .NET Core, .NET Framework, mono a UWP.

### <a name="net-core"></a>.NET Core

.NET Core je implementace rozhraní .NET pro víc platforem a navržená tak, aby zpracovávala úlohy serveru a cloudu ve velkém měřítku. Běží na Windows, macOS a Linux. Implementuje .NET Standard, takže kód, který cílí na .NET Standard, lze spustit v rozhraní .NET Core. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [model Windows Forms](../framework/winforms/windows-forms-overview.md)a [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) se spouštějí v .NET Core.

Další informace o .NET Core najdete v [příručce .NET Core](../core/index.md) a [Výběr mezi .net Core a .NET Framework pro serverové aplikace](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

The.NET Framework je původní implementace rozhraní .NET, která existuje od 2002. Je to stejná .NET Framework, že stávající vývojáři rozhraní .NET se vždycky používají. Verze 4,5 a novější implementují .NET Standard, takže kód, který cílí na .NET Standard, může běžet na těchto verzích .NET Framework. Obsahuje další rozhraní API specifická pro systém Windows, například rozhraní API pro vývoj desktopových aplikací pro Windows pomocí model Windows Forms a WPF. .NET Framework je optimalizovaná pro vytváření desktopových aplikací pro Windows.

Další informace o .NET Framework najdete v [průvodci .NET Framework](../framework/index.md).

### <a name="mono"></a>Mono

Mono je implementace rozhraní .NET, která se používá hlavně v případě, že je vyžadován malý modul runtime. Je to modul runtime, který využívá aplikace Xamarin na Androidu, macOS, iOS, tvOS a watchOS a zaměřuje se hlavně na malé nároky. Mono také vystavuje hry vytvořené pomocí modulu Unity.

Podporuje všechny aktuálně publikované verze .NET Standard.

V minulosti implementovala mono větší rozhraní API .NET Framework a emuluje některé z nejoblíbenějších funkcí v systému UNIX. Někdy se používá ke spouštění aplikací .NET, které spoléhají na tyto možnosti v systému UNIX.

Mono se obvykle používá s kompilátorem za běhu, ale také obsahuje úplný statický kompilátor (předem zkompilování), který se používá na platformách, jako je iOS.

Další informace o mono najdete v [dokumentaci k mono](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Univerzální platforma Windows (UPW)

UWP je implementace rozhraní .NET, která se používá k vytváření moderních, dotykové aplikace a softwaru Windows pro Internet věcí (IoT). Je navržený tak, aby sjednotí různé typy zařízení, na které můžete chtít cílit, včetně počítačů, tabletů, phablets, telefonů a i konzoly Xbox. UWP nabízí spoustu služeb, jako je centralizované úložiště aplikací, spouštěcí prostředí (kontejneru AppContainer) a sada rozhraní API systému Windows, které se mají použít místo Win32 (WinRT). Aplikace se dají zapisovat do C++, C#Visual Basic a JavaScriptu. Při použití C# a Visual Basic rozhraní API .NET poskytuje .NET Core.

Další informace o UWP najdete v tématu [Úvod do Univerzální platforma Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Moduly runtime .NET

Modul runtime je spouštěcí prostředí pro spravovaný program. Operační systém je součástí běhového prostředí, ale není součástí modulu .NET Runtime. Tady je několik příkladů prostředí .NET Runtime:

- Modul CLR (Common Language Runtime) pro .NET Framework
- Core Common Language Runtime (CoreCLR) pro .NET Core
- .NET Native pro Univerzální platforma Windows 
- Mono runtime pro Xamarin. iOS, Xamarin. Android, Xamarin. Mac a rozhraní mono Desktop Framework

## <a name="net-tooling-and-common-infrastructure"></a>Nástroje .NET a běžná infrastruktura

Máte přístup k rozsáhlé sadě nástrojů a komponent infrastruktury, které fungují při každé implementaci .NET. Patří mezi ně, ale nejsou omezeny na následující:

- Jazyky a jejich kompilátory .NET
- Systém projektu .NET (založený na souborech *. csproj*, *. vbproj*a *. fsproj* )
- [MSBuild](/visualstudio/msbuild/msbuild), modul sestavení používaný k sestavení projektů
- [NuGet](/nuget/), správce balíčků Microsoftu pro .NET
- Open Source nástroje pro orchestraci sestavení, například [dortíky](https://cakebuild.net/) a [napodobeniny](https://fake.build/)

## <a name="applicable-standards"></a>Příslušné standardy

Specifikace C# jazyka a Common Language Infrastructure (CLI) jsou standardizovány prostřednictvím [mezinárodní® ECMA](https://www.ecma-international.org/). První edice těchto standardů byly publikovány ECMA v prosinci 2001.

Další Revize standardů byly vyvinuty skupinami úloh TC49-TG2 (C#) a TC49-TG3 (CLI) v rámci technického výboru programovacích jazyků ([TC49](https://www.ecma-international.org/memento/tc49.htm)), které jsou přijaty obecným sestavením ECMA a následně podle normy ISO/IEC JTC 1 prostřednictvím procesu ISO Fast-Track.

### <a name="latest-standards"></a>Nejnovější standardy

Pro [C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm) rozhraní příkazového [řádku a CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) ([TR-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)) jsou k dispozici následující oficiální dokumenty ECMA:

- **Jazyk Standard (verze 5,0): ECMA-334. PDF C#**  [](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **Common Language Infrastructure**: Tato akce je k dispozici ve formátu [PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) a formuláři [zip](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip) .
- **Informace odvozené ze souboru XML oddílu IV**: je k dispozici ve formátech [PDF](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) a [zip](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip) .
 
Oficiální dokumenty ISO/IEC jsou k dispozici na stránce Standard ISO/IEC – [veřejně dostupné standardy](https://standards.iso.org/ittf/PubliclyAvailableStandards/) . Tyto odkazy jsou přímo z této stránky:

- **Informační technologie – programovací jazyky – C#** : [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **Informační technologie – oddíly Common Language Infrastructure (CLI) I až VI**: [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **Informační technologie – Common Language Infrastructure (CLI) – Technická zpráva o informacích odvozených ze souboru XML oddílu IV**: [ISO/IEC TR tr 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>Viz také

- [Volba mezi .NET Core a .NET Framework pro serverové aplikace](choosing-core-framework-server.md)
- [.NET Standard](net-standard.md)
- [Průvodce platformou .NET Core](../core/index.md)
- [Průvodce rozhraním .NET Framework](../framework/index.md)
- [Průvodce jazykem C#](../csharp/index.yml)
- [Průvodce jazykem F#](../fsharp/index.yml)
- [Průvodce jazykem Visual Basic](../visual-basic/index.yml)
