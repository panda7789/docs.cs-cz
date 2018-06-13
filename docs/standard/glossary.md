---
title: .NET – Glosář
description: Zjistěte význam vybrané termínů používaných v dokumentaci k rozhraní .NET.
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 195fbb799432b9d01a5faf301c9f8f2d1edfa1ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579402"
---
# <a name="net-glossary"></a>.NET – Glosář

Hlavním cílem, který tento glosář je objasnit významy vybrané podmínky a zkratky, které se zobrazují často v dokumentaci k rozhraní .NET bez definic.

## <a name="aot"></a>AOT

Napřed předčasné kompilátoru.

Podobně jako [JIT](#jit), tento kompilátoru také překládá [IL](#il) kódu počítače. Na rozdíl od JIT – kompilace probíhá kompilace AOT předtím, než se spustí aplikace a obvykle provádí na jiný počítač. Protože nástroj řetězy AOT nemáte kompilace za běhu, nemají minimalizovat čas strávený kompilace. To znamená, že se můžete tráví další optimalizace času. Vzhledem k tomu, že kontextu AOT bude celá aplikace se provádí kompilátoru AOT taky propojení mezi modulu a analýzy celého programu, což znamená, že všechny odkazy dodržíte a vytváří jeden spustitelný soubor.

## <a name="aspnet"></a>ASP.NET 

Původní implementace technologie ASP.NET, který se dodává s rozhraním .NET Framework.

Někdy ASP.NET je také souhrnný název, který odkazuje na obou implementace technologie ASP.NET, včetně ASP.NET Core. Což znamená, že termín představuje v jakékoli dané instanci je určen podle kontextu. Odkazovat na technologii ASP.NET 4.x, pokud chcete, aby bylo jasné, které nepoužívají ASP.NET rozumí obou implementace. 

V tématu [dokumentace k technologii ASP.NET](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Platformě, vysoce výkonné open source implementace technologie ASP.NET založený na .NET Core.

V tématu [ASP.NET Core dokumentaci](/aspnet/#pivot=core).

## <a name="assembly"></a>sestavení

A *.dll*/*.exe* soubor, který obsahuje kolekci rozhraní API, kterou lze volat aplikace nebo jiné sestavení.

Sestavení může obsahovat typy jako je rozhraní, třídy, struktury, výčty a delegáti. Sestavení v projektu *bin* složky se někdy označují jako *binární soubory*. Viz také [knihovny](#library).

## <a name="clr"></a>CLR

Modul Common Language Runtime.

Přesný význam závisí na kontext, ale to obvykle odkazuje na modul runtime rozhraní .NET Framework. Modul CLR zpracovává přidělování paměti a správu. Modul CLR je také virtuální počítač, který nejen spustí aplikace, ale také generuje a kompilovaný kód na průběžně pomocí JIT kompilátoru. Aktuální implementace Microsoft CLR je pouze v systému Windows.

## <a name="coreclr"></a>CoreCLR

.NET core modul Common Language Runtime.

Tato CLR je sestaven z stejný kód základní jako modulu CLR. Původně CoreCLR byl běhové prostředí Silverlight a byl navržen ke spuštění na více platforem, konkrétně Windows a OS X. CoreCLR je teď součástí .NET Core a představuje zjednodušenou verzi modulu CLR. Stále je nyní včetně podpory pro velkém množství distribucí Linux modulu runtime křížové platformy. Virtuální počítač s možností provádění JIT a kód je také CoreCLR.

## <a name="corefx"></a>CoreFX

Knihovny .NET core základní třídu (BCL)

Obory názvů sadu knihoven, které tvoří System.* (a v omezené míře Microsoft.*). BCL je obecné účely, nižší úrovně rozhraní, které vychází z vyšší úrovně rozhraní aplikace, jako je ASP.NET Core. Zdrojový kód BCL základní .NET je součástí [CoreFX úložiště](https://github.com/dotnet/corefx). Však většiny rozhraní API .NET Core jsou také k dispozici v rozhraní .NET Framework, proto si můžete představit CoreFX jako pokračovatelem BCL rozhraní .NET Framework.

## <a name="corert"></a>CoreRT

.NET core runtime.

Na rozdíl od CLR nebo CoreCLR, CoreRT není virtuální počítač, což znamená, neobsahuje zařízení pro generování a spuštění kódu na průběžně, protože neobsahuje [JIT](#jit). , Ale zahrnout [GC](#gc) a možnost identifikace typu modulu runtime (RTTI) a reflexe. Jeho systém typ je však navržené tak, aby metadata pro reflexi není povinné. Díky tomu, že [AOT](#aot) nástroj řetězec, který můžete propojit tokeny nadbytečné metadata a identifikovat (důležitější) kód, který nepoužívá aplikaci. CoreRT je ve vývoji.

V tématu [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="ecosystem"></a>ekosystém

Všechny runtime softwaru, nástroje pro vývoj a komunitní zdroje, které se používají k vytvoření a spuštění aplikace pro daný technologii.

Termín ".NET ekosystém" se liší od podobné podmínky, jako je například ".NET zásobníku" v jeho zahrnutí aplikacím třetích stran a knihovny. Tady je příklad ve větě:

- "Motivace za [.NET Standard](#net-standard) navázat větší jednotnost v ekosystému .NET." 

## <a name="framework"></a>rozhraní

Obecně platí komplexní kolekci rozhraní API, která usnadňuje vývoj a nasazení aplikací, které jsou založeny na konkrétní technologie. V této obecné smysl jsou příklady aplikační architektury ASP.NET Core a systém Windows Forms. Viz také [knihovny](#library).

Slovo "framework" má více zvláštní význam technické v následující podmínky:
* [.NET Framework](#net-framework)
* [Cílová architektura](#target-framework)
* [TFM (Přezdívka cílový framework)](#tfm)

Ve stávající dokumentaci "framework" někdy odkazuje [implementace rozhraní .NET](#implementation-of-net). Článek například může volat .NET Core rozhraní. Plánujeme toto matoucí použití v dokumentaci k odstranění.

## <a name="gc"></a>Uvolňování paměti

Systém uvolňování paměti.

Uvolňování paměti je implementací Automatická správa paměti.  Globální Katalog uvolní paměť obsazená objekty, které jsou již používán. 

V tématu [uvolňování paměti](garbage-collection/index.md).

## <a name="il"></a>IL

Převodní jazyk.

Vyšší úrovně jazyky rozhraní .NET, jako je C#, zkompilovat dolů sadu instrukcí bez ohledu na hardware, což se označuje jako zprostředkující jazyk (IL). IL se někdy označuje jako MSIL (Microsoft IL) nebo soubor CIL (běžné IL).

## <a name="jit"></a>JIT

Kompilátor za běhu.

Podobně jako [AOT](#aot), tento kompilátoru překládá [IL](#il) kódu počítače, která funguje s technologií procesoru. Na rozdíl od AOT JIT – kompilace probíhá na vyžádání a provádí na stejný počítač, který je potřeba spustit kód. Vzhledem k tomu, že JIT – kompilace dojde při spuštění aplikace, době potřebné ke kompilaci je součástí čas spuštění. Kompilátory JIT tedy mít vyvážit čas strávený optimalizace kódu proti úspory, který může vytvářet výsledný kód. Ale JIT zná skutečné hardwarové a můžete uvolnit vývojáři nemusíte se dodávají spolu různé implementace.

## <a name="implementation-of-net"></a>implementace rozhraní .NET

Implementace rozhraní .NET zahrnuje následující položky:

- Jeden nebo více moduly runtime. Příklady: CLR, CoreCLR, CoreRT.
- Knihovna tříd, který implementuje verzi .NET Standard a může zahrnovat další rozhraní API. Příklady: Knihovna rozhraní .NET Framework základní třídy, knihovny .NET Core základní třídy.
- Volitelně můžete jeden nebo více aplikací rozhraní. Příklady: ASP.NET, Windows Forms a WPF jsou zahrnuty v rozhraní .NET Framework.
- Volitelně můžete nástroje pro vývoj. Některé nástroje pro vývoj jsou sdílena mezi několika implementace.

Příklady implementace rozhraní .NET:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Univerzální platforma Windows (UPW)](#uwp)

## <a name="library"></a>knihovna

Sada rozhraní API, kterou lze volat aplikace nebo jiné knihovny. Knihovny .NET, se skládá z jednoho nebo více [sestavení](#assembly).

Knihovna slova a [framework](#framework) se často používají jako synonyma.

## <a name="metapackage"></a>metapackage

Balíček NuGet, který nemá žádné knihovny samostatně, ale je pouze seznam závislosti. Zahrnuté balíčky můžete volitelně vytvořit rozhraní API pro cílové rozhraní.

V tématu [balíčků, Metapackages a architektury](../core/packages.md)

## <a name="mono"></a>Mono

Mono je implementace rozhraní .NET, která se používá hlavně, když se vyžaduje malé runtime. Je modul runtime, která pohání aplikace Xamarin pro Android, Mac, iOS, tvOS a watchOS a se zaměřuje především na aplikace, které vyžadují malé nároky.

Podporuje všechny aktuálně publikovaná verze .NET Standard.

V minulosti Mono implementována větší rozhraní API rozhraní .NET Framework a emulovaných některé z nejčastěji používané funkcí v systému Unix. Někdy se používá ke spouštění aplikací .NET, které jsou závislé na tyto funkce v systému Unix.

Mono se obvykle používá s kompilátorem za běhu, ale nabízí i úplné statické kompilátoru (napřed předčasné kompilace), který se používá na platformách, jako je iOS.

Další informace o Mono, najdete v článku [Mono dokumentaci](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Termín zastřešující [.NET Standard](#net-standard) a všechny [implementace rozhraní .NET](#implementation-of-net) a úlohy. Vždy velkými písmeny, nikdy ".Net".

Najdete v článku [.NET Průvodce](index.md)

## <a name="net-core"></a>.NET Core 

Implementace rozhraní .NET a platformy, vysoce výkonné open source. Obsahuje základní Common Language Runtime (CoreCLR), AOT Core Runtime (vývojem CoreRT), základní základní knihovny tříd a Core SDK.

V tématu [.NET Core](../core/index.md).

## <a name="net-core-cli"></a>.NET core rozhraní příkazového řádku

Napříč platformami nástrojů pro vývoj aplikací .NET Core.

V tématu [nástrojů rozhraní příkazového řádku (CLI) .NET Core](../core/tools/index.md).

## <a name="net-core-sdk"></a>.NET core SDK

Sada knihovny a nástroje, které umožňují vývojářům vytvářet aplikace .NET Core a knihovny. Zahrnuje [.NET Core rozhraní příkazového řádku](#net-core-cli) pro vytváření aplikací, knihovny .NET Core a modulu runtime pro vytváření a spouštění aplikací a dotnet spustitelný soubor (*dotnet.exe*), spouští příkazy rozhraní příkazového řádku a spuštění aplikace.

V tématu [.NET Core SDK přehled](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Implementace rozhraní .NET, který spouští pouze v systému Windows. Zahrnuje Common Language Runtime (CLR), základní knihovny tříd a knihovny framework aplikace například ASP.NET, Windows Forms a WPF.

V tématu [rozhraní .NET Framework – průvodce](../framework/index.md).

## <a name="net-native"></a>.NET Native

Nástroj řetěz kompilátoru, která vytváří nativního kódu napřed předčasné (AOT), a v běhu (JIT).

Probíhá kompilace na počítači vývojáře, podobně jako C++ kompilátoru a linkeru funguje. Odebere nepoužívané kódu a stráví déle optimalizace ho. Extrahuje kód z knihovny a sloučí je do spustitelného souboru. Výsledkem je jeden modul, který představuje celou aplikaci.

UWP byla první rozhraní nepodporuje nativní rozhraní .NET. Teď podporujeme vytvářet nativní konzole aplikace pro Windows, systému macOS a Linux.

V tématu [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>Standardní rozhraní .NET

Formální specifikaci rozhraní API .NET, které jsou dostupné v každé implementace rozhraní .NET.

Specifikace .NET Standard, se někdy nazývá knihovnu v dokumentaci. Knihovnu zahrnuje implementace rozhraní API, ne jenom specifikace (rozhraní), a proto je zavádějící volat .NET Standard "knihovna". Plánujeme eliminovat toto využití z dokumentace, s výjimkou v souvislosti s aplikací název .NET Standard metapackage (`NETStandard.Library`).

V tématu [.NET Standard](net-standard.md).

## <a name="ngen"></a>NGEN

Generování nativních (obrázek).

Tato technologie si lze představit jako trvalé kompilátoru za běhu. Zkompiluje obvykle kódu na počítači, kde se spustí kód, ale kompilace obvykle dochází v době instalace.

## <a name="package"></a>Balíček

Balíček NuGet &mdash; nebo právě balíčku &mdash; je *.zip* soubor s jedno nebo více sestavení se stejným názvem spolu s další metadata, jako je například jméno autora.

*.Zip* soubor má *.nupkg* rozšíření a může obsahovat prostředky, jako například *.dll* soubory a *.xml* souborů pro použití s několika cílů rozhraní a verze. Při instalaci v aplikaci nebo knihovny, jsou vybrány příslušné prostředky založené na rozhraní target framework určeného aplikace nebo knihovny. Prostředky, které definují rozhraní jsou v *ref* složky a prostředky, které definují implementace *lib* složky.

## <a name="platform"></a>platforma

Operační systém a hardwaru, který běží na, například Windows, systému macOS, Linux, iOS a Android.

Zde jsou příklady využití v věty:

- ".NET core je implementace a platformy .NET." 
- "PCL profily představují platformy Microsoft, zatímco .NET Standard nerozlišuje platformy."

V rozhraní .NET dokumentaci často používá "Platformě .NET" rozumí buď implementace rozhraní .NET nebo zásobníku v rozhraní .NET, včetně všech implementace. Obě tyto použití často zmatení s primární význam (operačního systému nebo hardware), takže plánujeme tyto použití v dokumentaci k odstranění.

## <a name="runtime"></a>modul runtime

Spuštění prostředí spravované programu.

Je součástí běhové prostředí operačního systému, ale není součástí modulu runtime rozhraní .NET. Tady jsou některé příklady moduly runtime rozhraní .NET:

- Common Language Runtime (CLR)
- Základní Common Language Runtime (CoreCLR)
- .NET native (pro UPW)
- Monofonní runtime

V dokumentaci k rozhraní .NET, někdy používá "runtime" znamená úplně implementace rozhraní .NET. Například v následujícím věty "runtime" měl by být nahrazen "implementace":

- "Různé moduly runtime .NET implementovat určité verze .NET Standard."
- "Toto rozhraní by měl knihovny, které jsou určeny ke spuštění na víc runtimes cíle." (odkazující na .NET Standard)
- "Různé moduly runtime .NET implementovat určité verze .NET Standard. … Každou verzi modulu runtime .NET inzeruje nejvyšší .NET Standard verze, kterou podporuje..."

Plánujeme eliminovat toto nekonzistentní použití. 

## <a name="stack"></a>stack

Sada programování technologie, které se společně používají k sestavení a spuštění aplikace.

"Zásobníku .NET" odkazuje na všechny implementace rozhraní .NET a .NET Standard. Frázi ".NET zásobníku" mohou odkazovat na jednu implementaci rozhraní .NET. 

## <a name="target-framework"></a>Cílová architektura

Kolekce rozhraní API, která využívá aplikace .NET nebo knihovny.

Aplikace nebo knihovny, můžete vybrat verzi Standard .NET (například .NET standardní 2.0), což je specifikace pro standardizované sadu rozhraní API přes všechny implementace rozhraní .NET. Aplikace nebo knihovna můžete také cílení na verzi konkrétní implementace rozhraní .NET, ve které případ se získá přístup k rozhraní API pro konkrétní implementaci. Například aplikace, která je cílena Xamarin.iOS získá přístup k rozhraní API pro zadaný Xamarin iOS obálky.

Pro některé cílové rozhraní (například rozhraní .NET Framework) k dispozici rozhraní API jsou definovány sestavení, která nainstaluje rozhraní .NET implementace v systému, což může zahrnovat aplikační rozhraní API (například ASP.NET, WinForms). Rozhraní API pro balíček na základě cílové rozhraní (například .NET Standard a .NET Core), jsou definované balíčky nainstalované v aplikaci nebo knihovny. V takovém případě cílovém Frameworku, který určuje implicitně metapackage, který odkazuje na všechny balíčky, které společně tvoří rozhraní.

V tématu [cílové rozhraní](frameworks.md).

## <a name="tfm"></a>TFM

Cílový framework přezdívka.

Standardizovaná tokenu formát pro zadání cílové rozhraní aplikace .NET nebo knihovny. Cílové rozhraní jsou obvykle odkazuje krátký název, například `net462`. Dlouhá TFMs (například. NETFramework, verze = 4.6.2) existují, ale nejsou obecně používány k určení cílové rozhraní.

V tématu [cílové rozhraní](frameworks.md).

## <a name="uwp"></a>UWP

Univerzální platformy Windows.

Implementace rozhraní .NET, který se používá pro vytváření moderní, dotykovým ovládáním aplikace systému Windows a software pro Internet věcí (IoT). Je určený ke sjednocení různé typy zařízení, které chcete zacílit, včetně počítače, tablety, phablets, telefony a i Xbox. UWP poskytuje mnoho služeb, jako je například centralizované app storu, prostředí provádění (AppContainer) a sadu rozhraní API systému Windows tak, aby používal místo Win32 (WinRT). Aplikace může být napsané v jazyce C++, C#, VB.NET a JavaScript. Při použití jazyka C# a VB.NET, rozhraní API .NET jsou poskytovány .NET Core.

## <a name="see-also"></a>Viz také

[Průvodce technologií .NET](index.md)  
[Průvodce rozhraním .NET Framework](../framework/index.md)  
[.NET Core](../core/index.md)  
[Přehled technologie ASP.NET](/aspnet/index#pivot=aspnet)  
[Přehled ASP.NET Core](/aspnet/index#pivot=core)  

