---
title: Architekturálních komponentách .NET
description: Popisuje architekturálních komponentách .NET například .NET Standard, implementace .NET, moduly runtime .NET a nástroje.
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: e131ab48b666f2d22d8bd02e41ed76e415a2597d
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323714"
---
# <a name="net-architectural-components"></a>Architekturálních komponentách .NET

Je vyvinutý pro aplikace .NET a běží v jedné nebo více *implementace .NET*.  Implementace .NET zahrnout rozhraní .NET Framework, Mono a .NET Core. Společné pro všechny implementace .NET, které se nazývá .NET Standard je specifikace rozhraní API. Tento článek přináší stručný úvod ke každé z těchto konceptů.

## <a name="net-standard"></a>.NET standard

.NET Standard je sada rozhraní API, které jsou implementované základní knihovny tříd .NET implementace. Více formálně je specifikace rozhraní API .NET, která tvoří sadu smluv, které kompilaci kódu proti jednotné. Tyto smlouvy jsou implementovány v každé implementace .NET. To umožňuje přenositelnost napříč různými implementacemi .NET umožňuje efektivně váš kód běžet kdekoli.

.NET Standard se také [Cílová architektura](glossary.md#target-framework). Pokud váš kód cílí na verzi .NET Standard, můžete spustit v jakékoli implementaci rozhraní .NET, což podporuje danou verzi .NET Standard.

Další informace o .NET Standard a jak se zaměřit na to, najdete v článku [.NET Standard](net-standard.md) tématu.

## <a name="net-implementations"></a>Implementace .NET

Každá implementace .NET obsahuje následující součásti:

- Jeden nebo více modulů runtime. Příklady: CLR pro rozhraní .NET Framework, CoreCLR a CoreRT pro .NET Core.
- Knihovny tříd .NET Standard a může implementovat další rozhraní API. Příklady: Základní knihovny tříd .NET Framework, knihovně základních tříd .NET Core.
- Volitelně můžete jeden nebo více aplikačních architektur. Příklady: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md), a [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) jsou zahrnuty v rozhraní .NET Framework.
- Volitelně můžete nástroje pro vývoj. Některé vývojové nástroje jsou sdíleny více implementací.

Existují čtyři primární implementace .NET, které Microsoft aktivně vyvíjí a udržuje: .NET Core, .NET Framework, Mono a UPW.

### <a name="net-core"></a>.NET Core

.NET core je na více platforem implementace rozhraní .NET a určený pro zpracování úloh serverová a Cloudová ve velkém měřítku. Běží na Windows, macOS a Linux. .NET Standard, implementuje tak kód, který cílí na .NET Standard můžete spustit na .NET Core. ASP.NET Core běží na .NET Core. 

Další informace o .NET Core, najdete v článku [Průvodce platformou .NET Core](../core/index.md) a [volba mezi .NET Core a .NET Framework pro serverové aplikace](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

Rozhraní.NET Framework je původní implementace .NET, která již od 2002. Je stávající vývojáře na platformě .NET mají vždy používá stejné rozhraní .NET Framework. Verze 4.5 a vyšší implementace .NET Standard, tak kód, který cílí na .NET Standard můžete spustit v těchto verzích rozhraní .NET Framework. Obsahuje další rozhraní API specifické pro Windows, jako je například rozhraní API pro Windows vývoj desktopových aplikací pomocí Windows Forms a WPF. Rozhraní .NET Framework je optimalizovaný pro vytváření aplikací klasické pracovní plochy Windows.

Další informace o rozhraní .NET Framework, najdete v článku [rozhraní .NET Framework – průvodce](../framework/index.md).

### <a name="mono"></a>Mono

Mono je implementace .NET, který se používá hlavně při malý modul runtime je povinný. Je modul runtime, který zajišťuje provoz aplikací v Xamarinu na Android, Mac, iOS, tvOS a watchOS a zaměřili hlavně na malou stopu. Mono také využívají hry vytvořené pomocí modulu Unity.

Podporuje všechny aktuálně publikované verze .NET Standard.

V minulosti Mono implementovaná větší API rozhraní .NET Framework a emulované některé z nejoblíbenějších funkcí v systému Unix. Někdy se používá ke spouštění aplikací .NET, které využívají tyto funkce v systému Unix.

Mono se obvykle používá s kompilátorem za běhu, ale obsahuje taky celý statický kompilátor (ahead of time kompilace), který se používá na platformách, jako je iOS.

Další informace o Mono, najdete v článku [dokumentace Mono](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Univerzální platforma Windows (UPW)

UPW je implementace .NET, která je určená k vytváření moderních, dotykově ovládaný Windows aplikací a softwaru pro Internet věcí (IoT). Je určený ke sjednocení různé typy zařízení, které můžete chtít zaměřit, včetně počítače, tablety, phablets, telefony a dokonce i Xbox. UPW poskytuje mnoho služeb, jako jsou centralizované app storu, spouštěcí prostředí (AppContainer) a sada rozhraní API Windows nahrazujícím Win32 (WinRT). Aplikace může být napsané v jazyce C++, C#, VB.NET a JavaScript. Při použití jazyka C# a VB.NET, jsou k dispozici rozhraní API .NET pomocí .NET Core.

Další informace o UPW, naleznete v tématu [Úvod k univerzální platformě Windows](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Moduly .NET runtime

Modul runtime je prostředí pro spuštění spravované aplikace. Operační systém je součástí prostředí modulu runtime, ale není součástí modulu runtime .NET. Tady je několik příkladů moduly runtime .NET:

- Common Language Runtime (CLR) pro rozhraní .NET Framework
- Základní modul Common Language Runtime (CoreCLR) pro .NET Core
- .NET native pro Universal Windows Platform 
- Modul Mono runtime pro Xamarin.iOS, Xamarin.Android, Xamarin.Mac a Mono framework klasické pracovní plochy

## <a name="net-tooling-and-common-infrastructure"></a>Nástroje pro .NET a běžnou infrastrukturu

Máte přístup k rozsáhlé sadu nástrojů a komponent infrastruktury, které fungují s každou implementace .NET. Ty zahrnují, ale nejsou omezeny na následující:

- Jazyky rozhraní .NET a jejich kompilátory
- Systém projektu .NET (na základě *.csproj*, *.vbproj*, a *.fsproj* soubory)
- [Nástroj MSBuild](/visualstudio/msbuild/msbuild), modul sestavení použít k sestavení projektů
- [NuGet](/nuget/), Správce balíčků od Microsoftu pro .NET
- Orchestrace sestavení Open source nástroje, jako například [DORT](https://cakebuild.net/) a [FALEŠNÉ](https://fake.build/)

## <a name="see-also"></a>Viz také:

- [Volba mezi .NET Core a .NET Framework pro serverové aplikace](choosing-core-framework-server.md)   
- [.NET Standard](net-standard.md)  
- [Průvodce platformou .NET Core](../core/index.md)  
- [Průvodce rozhraním .NET Framework](../framework/index.md)  
- [Průvodce jazykem C#](../csharp/index.md)  
- [Průvodce jazykem F#](../fsharp/index.md)  
- [Průvodce VB.NET](../visual-basic/index.md)  
