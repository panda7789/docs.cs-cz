---
title: Součástí architektury .NET
description: Popisuje architektury součásti rozhraní .NET, například .NET Standard, implementace rozhraní .NET, moduly runtime rozhraní .NET a nástroje.
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 51e6779d63cdaccc5633c9e81f97471d71099653
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="net-architectural-components"></a>Součástí architektury .NET

Vyvinutý pro aplikace .NET a běží v jedné nebo více *implementace rozhraní .NET*.  Implementace rozhraní .NET zahrnují rozhraní .NET Framework, .NET Core a Mono. Společné pro všechny implementace rozhraní .NET, která je volána .NET Standard je specifikace rozhraní API. Tento článek poskytuje stručný úvod do každé z těchto položek.

## <a name="net-standard"></a>Standardní rozhraní .NET

.NET Standard je sada rozhraní API, které jsou implementované základní knihovna tříd rozhraní .NET implementace. Více oficiálně je specifikace rozhraní API .NET, která tvoří sadu uniform smluv, které zkompilujete svůj kód s. Tyto smlouvy jsou implementované v každé implementace rozhraní .NET. To umožňuje přenosnost napříč různými implementacemi .NET, efektivně umožňující spustit everywhere kódu.

.NET Standard je také [cílové rozhraní](glossary.md#target-framework). V případě kódu cílovou verzi .NET Standard, můžete spustit na jakékoli implementace rozhraní .NET, která podporuje tuto verzi .NET Standard.

Další informace o standardní rozhraní .NET a jak ho mít najdete v tématu [.NET Standard](net-standard.md) tématu.

## <a name="net-implementations"></a>Implementace rozhraní .NET

Každá implementace rozhraní .NET zahrnuje následující součásti:

- Jeden nebo více moduly runtime. Příklady: CLR rozhraní .NET Framework, CoreCLR a CoreRT pro .NET Core.
- Knihovna tříd, který implementuje standardní rozhraní .NET a může implementovat další rozhraní API. Příklady: Knihovna rozhraní .NET Framework základní třídy, knihovny .NET Core základní třídy.
- Volitelně můžete jeden nebo více aplikací rozhraní. Příklady: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md), a [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) jsou zahrnuty v rozhraní .NET Framework.
- Volitelně můžete nástroje pro vývoj. Některé nástroje pro vývoj jsou sdílena mezi několika implementace.

Existují čtyři primární implementace rozhraní .NET, které Microsoft aktivně vyvíjí a udržuje: .NET Core, rozhraní .NET Framework, Mono a UWP.

### <a name="net-core"></a>.NET Core

.NET core je implementace a platformy .NET a určený k řešení serveru a cloudu, škálované úlohy. Běží na systému Windows, systému macOS a Linux. Rozhraní .NET standardní implementuje tak kód, který cílí na Standard .NET můžete spustit na .NET Core. ASP.NET Core běží na .NET Core. 

Další informace o .NET Core, najdete v článku [.NET Core průvodce](../core/index.md) a [výběru mezi .NET Core a rozhraní .NET Framework pro server aplikace](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

Rozhraní.NET Framework je původní implementace rozhraní .NET, která již od 2002. Je stejné rozhraní .NET Framework, který mají vždy použít existující vývojáře .NET. Verze 4.5 a novější implementace .NET Standard, tak kód, který cílí na Standard .NET můžete spustit tyto verze rozhraní .NET Framework. Obsahuje další rozhraní API specifické pro systém Windows, jako je například vývoj aplikací API pro systém Windows s Windows Forms a WPF. Rozhraní .NET Framework je optimalizovaná pro vytváření aplikací klasické pracovní plochy Windows.

Další informace o rozhraní .NET Framework, najdete v článku [rozhraní .NET Framework – průvodce](../framework/index.md).

### <a name="mono"></a>Mono

Mono je implementace rozhraní .NET, která se používá hlavně, když se vyžaduje malé runtime. Je modul runtime, která pohání aplikace Xamarin pro Android, Mac, iOS, tvOS a watchOS a se zaměřuje především na malé nároky. Mono také zajišťuje hry vytvořené pomocí modulu Unity.

Podporuje všechny aktuálně publikovaná verze .NET Standard.

V minulosti Mono implementována větší rozhraní API rozhraní .NET Framework a emulovaných některé z nejčastěji používané funkcí v systému Unix. Někdy se používá ke spouštění aplikací .NET, které jsou závislé na tyto funkce v systému Unix.

Mono se obvykle používá s kompilátorem za běhu, ale nabízí i úplné statické kompilátoru (napřed předčasné kompilace), který se používá na platformách, jako je iOS.

Další informace o Mono, najdete v článku [Mono dokumentaci](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Univerzální platforma Windows (UPW)

UWP je implementací rozhraní .NET, který se používá pro vytváření moderní, dotykovým ovládáním aplikace systému Windows a software pro Internet věcí (IoT). Je určený ke sjednocení různé typy zařízení, které chcete zacílit, včetně počítače, tablety, phablets, telefony a i Xbox. UWP poskytuje mnoho služeb, jako je například centralizované app storu, prostředí provádění (AppContainer) a sadu rozhraní API systému Windows tak, aby používal místo Win32 (WinRT). Aplikace může být napsané v jazyce C++, C#, VB.NET a JavaScript. Při použití jazyka C# a VB.NET, rozhraní API .NET jsou poskytovány .NET Core.

Další informace o UWP najdete v tématu [Úvod do univerzální platformy Windows](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Moduly runtime rozhraní .NET

Modul runtime je prostředí pro spuštění programu spravované. Je součástí běhové prostředí operačního systému, ale není součástí modulu runtime rozhraní .NET. Tady jsou některé příklady moduly runtime rozhraní .NET:
 
 - Common Language Runtime (CLR) pro rozhraní .NET Framework
 - Základní modul Common Language Runtime (CoreCLR) pro .NET Core
 - .NET native pro univerzální platformu Windows 
 - Monofonní modul runtime pro Xamarin.iOS, Xamarin.Android, Xamarin.Mac a Mono desktopového rozhraní

## <a name="net-tooling-and-common-infrastructure"></a>Nástroje rozhraní .NET a běžnou infrastrukturu

Máte přístup k rozsáhlou sadu nástrojů a součásti infrastruktury, které fungují s každou implementace rozhraní .NET. Ty zahrnují, ale nejsou omezeny na následující:

- Jazyky rozhraní .NET a jejich kompilátory
- Systém .NET projektu (na základě *.csproj*, *.vbproj*, a *.fsproj* soubory)
- [MSBuild](/visualstudio/msbuild/msbuild), modul sestavení použitý k sestavení projektů
- [NuGet](/nuget/), Správce balíčků společnosti Microsoft pro rozhraní .NET
- Orchestration sestavení Open source nástrojů, jako je například [DORT](https://cakebuild.net/) a [ZFALŠOVAT](https://fake.build/)

## <a name="see-also"></a>Viz také
[Volba mezi .NET Core a rozhraní .NET Framework pro server aplikace](choosing-core-framework-server.md)   
[.NET Standard](net-standard.md)  
[Průvodce platformou .NET Core](../core/index.md)  
[Průvodce rozhraním .NET Framework](../framework/index.md)  
[Průvodce jazykem C#](../csharp/index.md)  
[Průvodce jazykem F#](../fsharp/index.md)  
[Průvodce VB.NET](../visual-basic/index.md)  

