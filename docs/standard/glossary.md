---
title: Slovníček k technologii .NET
description: Zjistěte význam vybraných termínů používaných v dokumentaci .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 59e338de99510759e3e7acfd782915ed6dc5d988
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957570"
---
# <a name="net-glossary"></a>Slovníček k technologii .NET

Hlavním cílem tohoto glosáře je objasnit význam vybraných termínů a zkratek, které se v dokumentaci .NET často objevují bez definic.

## <a name="aot"></a>AOT

Předem-včas kompilátor.

Podobně jako [JIT](#jit), tento kompilátor také překládá [Il](#il) do strojového kódu. Na rozdíl od kompilace JIT proběhne kompilace AOT před provedením aplikace a obvykle se provádí v jiném počítači. Vzhledem k tomu, že řetězy nástrojů AOT nejsou kompilovány za běhu, nemusí minimalizovat čas strávený kompilací. To znamená, že můžou věnovat více času optimalizaci. Vzhledem k tomu, že kontext AOT je celá aplikace, provede kompilátor AOT také propojení mezi moduly a analýzou celého programu, což znamená, že jsou následovány všechny odkazy a je vytvořen jediný spustitelný soubor.

Viz [CoreRT](#corert) a [.NET Native](#net-native).

## <a name="aspnet"></a>ASP.NET

Původní implementace ASP.NET, která je dodávána s .NET Framework.

Někdy ASP.NET je zastřešující termín, který odkazuje na implementace ASP.NET, včetně ASP.NET Core. To znamená, že podmínka přenáší v rámci určité instance je určena podle kontextu. Pokud chcete, aby bylo jasné, že nepoužíváte ASP.NET, použijte k tomu ASP.NET 4. x, které by znamenaly obě implementace.

Další informace najdete v [dokumentaci k ASP.NET](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>Jádro ASP.NET

Vysoce výkonná a open source implementace ASP.NET pro více platforem.

Viz [dokumentace ASP.NET Core](/aspnet/#pivot=core).

## <a name="assembly"></a>sestavení

Soubor *. dll* / *. exe* , který může obsahovat kolekci rozhraní API, která mohou být volána aplikacemi nebo jinými sestaveními.

Sestavení může obsahovat typy, jako jsou rozhraní, třídy, struktury, výčty a Delegáti. Sestavení ve složce *bin* projektu jsou někdy označována jako *binární soubory*. Viz také [Knihovna](#library).

## <a name="bcl"></a>BCL

Základní knihovna tříd. Označují se také jako *knihovny rozhraní*.

Sada knihoven, které tvoří systém. \* (a do omezeného rozsahu Microsoft. \* ) obsažené. BCL je pro obecné účely rozhraní nižší úrovně, které používá aplikační architektury vyšší úrovně, například ASP.NET Core, sestavení.

Zdrojový kód BCL pro [.NET 5 (a .NET Core) a novější verze](#net-5-and-later-versions) je obsažen v [úložišti modulu .NET runtime](https://github.com/dotnet/runtime). Většina rozhraní BCL API pro tuto novější implementaci rozhraní .NET je také k dispozici v .NET Framework, takže si tento zdrojový kód můžete představit jako rozvětvení zdrojového kódu .NET Framework BCL.

## <a name="clr"></a>CLR

Modul CLR (Common Language Runtime)

Přesný význam závisí na kontextu. Modul CLR (Common Language Runtime) obvykle odkazuje na modul runtime [.NET Framework](#net-framework) nebo modul runtime [rozhraní .NET 5 (a .NET Core) a novějších verzí](#net-5-and-later-versions).

Modul CLR zpracovává přidělování a správu paměti. CLR je také virtuálním počítačem, který nespouští pouze aplikace, ale také generuje a kompiluje kód průběžně pomocí kompilátoru [JIT](#jit) .

Implementace CLR pro .NET Framework je pouze Windows.

Implementace CLR pro .NET 5 a novější verze (označovaná také jako základní CLR) je sestavena ze stejného základu kódu jako modul CLR .NET Framework. Základní CLR byl původně modulem runtime programu Silverlight a byl navržen pro spouštění na více platformách, konkrétně v systému Windows a OS X. Je to pořád modul runtime pro [více platforem](#cross-platform) , který teď zahrnuje podporu pro spoustu distribucí Linux.

Viz také [modul runtime](#runtime).

## <a name="core-clr"></a>Core CLR

Modul CLR (Common Language Runtime [) pro .NET 5 (a .NET Core) a novější verze](#net-5-and-later-versions).

Viz [CLR](#clr)

## <a name="corert"></a>CoreRT

Na rozdíl od [CLR](#clr)není CoreRT virtuálním počítačem, což znamená, že nezahrnuje zařízení pro generování a běh kódu průběžně, protože nezahrnuje [JIT](#jit). Nicméně obsahuje [GC](#gc) a možnost identifikace typu za běhu (RTTI) a reflexe. Nicméně systém jeho typů je navržen tak, aby se metadata pro reflexi nevyžadovala. Nevyžadování metadat umožňuje mít řetěz nástrojů [AOT](#aot) , který může propojit nadbytečné metadata a (důležitější je) identifikovat kód, který aplikace nepoužívá. CoreRT je ve vývoji.

Přečtěte si [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).

## <a name="cross-platform"></a>pro různé platformy

Možnost vyvíjet a spouštět aplikaci, která se dá použít v několika různých operačních systémech, jako jsou Linux, Windows a iOS, aniž by se musely přepsat speciálně pro každé z nich. To umožňuje opakované použití kódu a konzistenci mezi aplikacemi na různých platformách.

## <a name="ecosystem"></a>ekosystému

Veškerý běhový software, vývojové nástroje a komunitní prostředky, které se používají k sestavování a spouštění aplikací pro danou technologii.

Pojem "ekosystém .NET" se od podobných termínů, jako je například .NET Stack, liší v zahrnutí aplikací a knihoven třetích stran. Tady je příklad ve větě:

- "Motivací za [.NET Standard](#net-standard) je vytvoření větší jednotnosti v ekosystému .NET."

## <a name="framework"></a>rozhraní

Obecně platí komplexní kolekce rozhraní API, která usnadňují vývoj a nasazování aplikací, které jsou založeny na konkrétní technologii. V tomto obecném smyslu jsou příklady aplikačních rozhraní ASP.NET Core a model Windows Forms. Viz také [Knihovna](#library).

Slovo "Framework" má v následujících termínech jiný význam:

- [.NET Framework](#net-framework)
- [Cílová architektura](#target-framework)
- [TFM (moniker cílového rozhraní .NET Framework)](#tfm)
- [aplikace závislá na rozhraní](../core/deploying/index.md#publish-framework-dependent)

V dokumentaci k starší verzi rozhraní .NET "rozhraní" někdy odkazuje na [implementaci rozhraní .NET](#implementation-of-net). Například článek může volat rozhraní .NET 5 a Framework.

## <a name="gc"></a>Uvolňování paměti

Systém uvolňování paměti.

Systém uvolňování paměti je implementace automatické správy paměti.  GC uvolňuje paměť obsazená objekty, které se již nepoužívají.

Viz [shromažďování paměti](garbage-collection/index.md).

## <a name="il"></a>IL

Převodní jazyk.

Jazyky vyšší úrovně .NET, jako je C#, se zkompiluje do nezávislá sady instrukcí pro hardware, která se označuje jako Intermediate Language (IL). IL se někdy označuje jako MSIL (Microsoft IL) nebo CIL (Common IL).

## <a name="jit"></a>JIT

Kompilátor za běhu.

Podobně jako [AOT](#aot)tento kompilátor překládá [Il](#il) na strojový kód, který procesor rozumí. Na rozdíl od AOT probíhá kompilace JIT na vyžádání a je provedena na stejném počítači, na kterém je nutné kód spustit. Vzhledem k tomu, že během provádění aplikace dojde k kompilaci JIT, doba kompilace je součástí doby běhu. Kompilátory JIT proto musí vyvážit čas strávený optimalizací kódu proti úsporám, které může výsledný kód vyvolat. Kompilátor JIT ale zná skutečný hardware a může vývojářům zdarma dodávat různé implementace.

## <a name="implementation-of-net"></a>implementace rozhraní .NET

Implementace rozhraní .NET zahrnuje:

- Jeden nebo více modulů runtime. Příklady: [CLR](#clr), [CoreRT](#corert).
- Knihovna tříd, která implementuje verzi .NET Standard a může obsahovat další rozhraní API. Příklady: [BCLs](#bcl) pro [.NET Framework](#net-framework) a [.NET 5 (a .NET Core) a novější verze](#net-5-and-later-versions).
- Volitelně jeden nebo více aplikačních architektur. Příklady: [ASP.NET](#aspnet), model Windows Forms a WPF jsou součástí .NET Framework a .NET 5.
- Volitelně vývojové nástroje. Některé vývojové nástroje se sdílejí mezi více implementacemi.

Příklady implementací rozhraní .NET:

- [.NET Framework](#net-framework)
- [.NET 5 a novější verze (včetně .NET Core 2.1-3.1](#net-5-and-later-versions)
- [Univerzální platforma Windows (UPW)](#uwp)
- [Mono](#mono)

## <a name="library"></a>knihovna

Kolekce rozhraní API, která mohou být volána aplikacemi nebo jinými knihovnami. Knihovna .NET se skládá z jednoho nebo více [sestavení](#assembly).

Slova Library a [Framework](#framework) se často používají jako synonyma.

## <a name="mono"></a>Mono

Mono je open source implementace .NET pro [různé platformy](#cross-platform) , která se používá hlavně v případě, že je potřeba malý modul runtime. Je to modul runtime, který vychází z aplikací Xamarin na zařízeních s Androidem, Mac, iOS, tvOS a watchOS a primárně se zaměřuje na aplikace, které vyžadují malé nároky.

Podporuje všechny aktuálně publikované verze .NET Standard.

V minulosti implementovala mono větší rozhraní API .NET Framework a emuluje některé z nejoblíbenějších funkcí v systému UNIX. Někdy se používá ke spouštění aplikací .NET, které spoléhají na tyto možnosti v systému UNIX.

Mono se obvykle používá s [kompilátorem za běhu](#jit), ale také obsahuje úplný [statický kompilátor (předem zkompilování)](#aot) , který se používá na platformách, jako je iOS.

Podívejte se na [dokumentaci k mono](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Termín pro [.NET Standard](#net-standard) a všechny implementace a úlohy [.NET](#implementation-of-net) . Vždy plně velkými písmeny, nikdy ".NET".

Když se uvolní [.NET 5](#net-5-and-later-versions) (aktuálně ve verzi Preview), bude doporučená implementace .NET pro všechny nové vývojové prostředí .NET, takže v některých kontextech ".NET" bude znamenat ".NET 5 a novější verze".

Projděte si [příručku .NET](index.yml)

## <a name="net-5-and-later-versions"></a>.NET 5 a novější verze

Vysoce výkonná a open source implementace .NET pro více platforem. Zahrnuje modul[CLR](#clr)(Common Language Runtime), modul runtime [AOT](#aot) ([CoreRT](#corert), ve vývoji), knihovnu základní třídy ([BCL](#bcl)) a [sadu .NET SDK](#net-sdk).

Starší verze této implementace rozhraní .NET se označují jako .NET Core. .NET 5,0 je další verze, která následuje po .NET Core 3,1. Verze 4 byla vynechána, aby nedocházelo k matoucí této novější implementace .NET se starší implementací, která se označuje jako [.NET Framework](#net-framework). Aktuální verze .NET Framework je 4,8.

Viz [.NET](../core/index.yml).

## <a name="net-cli"></a>ROZHRANÍ .NET CLI

Sada nástrojů pro více platforem pro vývoj aplikací a knihoven pro [.NET 5 (a .NET Core) a novější verze](#net-5-and-later-versions). Označuje se také jako .NET Core CLI.

Viz [rozhraní .NET CLI](../core/tools/index.md).

## <a name="net-core"></a>.NET Core

Viz [.NET 5 a novější verze](#net-5-and-later-versions).

## <a name="net-framework"></a>.NET Framework

Implementace rozhraní .NET, která běží pouze v systému Windows. Zahrnuje modul[CLR](#clr)(Common Language Runtime), knihovnu základních tříd ([BCL](#bcl)) a knihovny aplikačních rozhraní, jako je například [ASP.NET](#aspnet), model Windows Forms a WPF.

Viz [průvodce .NET Framework](../framework/index.yml).

## <a name="net-native"></a>.NET Native

Řetěz nástrojů kompilátoru, který vytváří nativní kód před časem ([AOT](#aot)), na rozdíl od[JIT](#jit)(just-in-time).

Kompilace probíhá na počítači vývojáře podobně jako kompilátor jazyka C++ a linker funguje. Odebírá nepoužitý kód a stráví více času optimalizací. Extrahuje kód z knihoven a sloučí je do spustitelného souboru. Výsledkem je jeden modul, který představuje celou aplikaci.

UWP byla první aplikační architektura, kterou .NET Native podporuje. Nyní podporujeme vytváření nativních konzolových aplikací pro Windows, macOS a Linux.

Viz [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-sdk"></a>.NET SDK

Sada knihoven a nástrojů, které vývojářům umožňují vytvářet aplikace a knihovny .NET pro [rozhraní .NET 5 (a .NET Core) a novější verze](#net-5-and-later-versions). Označuje se také jako .NET Core SDK.

Zahrnuje [rozhraní .NET CLI](#net-cli) pro vytváření aplikací, knihovny .NET a běhové prostředí pro sestavování a spouštění aplikací a spustitelný soubor dotnet (*dotnet.exe*), který spouští příkazy rozhraní příkazového řádku a spouští aplikace.

Viz [Přehled sady .NET SDK](../core/sdk.md).

## <a name="net-standard"></a>.NET Standard

Formální specifikace rozhraní .NET API, které jsou k dispozici v každé implementaci rozhraní .NET.

Specifikace .NET Standard se v dokumentaci někdy označuje jako knihovna. Vzhledem k tomu, že knihovna obsahuje implementace rozhraní API, nikoli pouze specifikace (rozhraní), je pro volání .NET Standard "Library" zavádějící.

Viz [.NET Standard](net-standard.md).

## <a name="ngen"></a>NGEN

Generování nativních (imagí)

Tuto technologii si můžete představit jako trvalý kompilátor [JIT](#jit) . Obvykle kompiluje kód na počítači, kde je spuštěn kód, ale kompilace obvykle probíhá v době instalace.

## <a name="package"></a>balíček

Balíček NuGet &mdash; nebo pouze balíček &mdash; je soubor *. zip* s jedním nebo více sestaveními se stejným názvem společně s dalšími metadaty, jako je jméno autora.

Soubor *. zip* má příponu *. nupkg* a může obsahovat prostředky, jako jsou soubory *DLL* a *XML* soubory pro použití s více cílovými rozhraními a verzemi. Při instalaci v aplikaci nebo knihovně jsou příslušné prostředky vybrány na základě cílového rozhraní určeného aplikací nebo knihovnou. Prostředky, které definují rozhraní, jsou ve složce *ref* a assety definující implementaci jsou ve složce *lib* .

## <a name="platform"></a>platforma

Operační systém a hardware, na kterém běží, jako je Windows, macOS, Linux, iOS a Android.

Tady jsou příklady použití ve větách:

- ".NET Core je implementace .NET pro různé platformy."
- "Profily PCL reprezentují platformy Microsoft, zatímco .NET Standard nezávislá na platformu."

Starší verze dokumentace rozhraní .NET někdy používá "platformu .NET" k označení [implementace .NET](#implementation-of-net) nebo [zásobníku](#stack) .NET, včetně všech implementací. Obě tato použití se od sebe snaží získat zaměňovatelné s primárním (operačním nebo hardwarovým) významem, takže se z těchto použití vyhneme.

Pojem "platforma" má v frázi "vývojářské platformy" jiný význam, který odkazuje na software, který poskytuje nástroje a knihovny pro sestavování a spouštění aplikací. .NET je open source platforma pro vývoj na různých platformách pro vytváření mnoha různých typů aplikací.

## <a name="runtime"></a>modul runtime

Obecně platí, že spouštěcí prostředí pro spravovaný program. Operační systém je součástí běhového prostředí, ale není součástí modulu .NET Runtime. Tady je několik příkladů prostředí .NET runtime v tomto smyslu slova:

- Modul[CLR](#clr)(Common Language Runtime)
- .NET Native (pro UWP)
- Mono runtime

Slovo "runtime" má v následujících kontextech jiný význam:

* [Stránka pro stažení rozhraní .NET](https://dotnet.microsoft.com/download).

  "Modul runtime" zde znamená [CLR](#clr) společně s knihovnou [BCL](#bcl) (architektury Framework), které si můžete stáhnout a nainstalovat na počítač, abyste mohli na počítači spouštět aplikace [závislé na architektuře](../core/deploying/index.md#publish-framework-dependent) .

* [Identifikátor modulu runtime (RID)](../core/rid-catalog.md) pro [rozhraní .NET 5 (a .NET Core) a novější verze](#net-5-and-later-versions).

  "Za běhu" se rozumí platforma operačního systému a architektura procesoru, na které běží aplikace .NET, například: `linux-x64` .

Starší verze dokumentace rozhraní .NET někdy používá "modul runtime" v tom smyslu [implementace .NET](#implementation-of-net), jako v následujících příkladech:

- "Různé moduly runtime .NET implementují konkrétní verze .NET Standard."
- "Knihovny určené ke spuštění na více modulech runtime by měly cílit na toto rozhraní." (odkazování na .NET Standard)
- "Různé moduly runtime .NET implementují konkrétní verze .NET Standard. … Každá verze modulu .NET runtime inzeruje nejvyšší .NET Standard verzi, kterou podporuje...

## <a name="stack"></a>stack

Sada programovacích technologií používaných společně k sestavování a spouštění aplikací.

Rozhraní .NET Stack odkazuje na .NET Standard a všechny implementace rozhraní .NET. Fráze ".NET Stack" může odkazovat na jednu implementaci rozhraní .NET.

## <a name="target-framework"></a>Cílová architektura

Kolekce rozhraní API, na kterých závisí aplikace .NET nebo knihovna

Aplikace nebo knihovna může cílit na verzi .NET Standard (například .NET Standard 2,0), což je specifikace standardizované sady rozhraní API napříč všemi implementacemi .NET. Aplikace nebo knihovna může také cílit na verzi konkrétní implementace rozhraní .NET. v takovém případě získá přístup k rozhraním API pro konkrétní implementaci. Například aplikace, která se zaměřuje na Xamarin. iOS, získá přístup k obálkám rozhraní API iOS poskytovaných v Xamarin.

Pro některé cílové architektury (například .NET Framework) jsou dostupná rozhraní API definovaná sestaveními, která implementuje implementace rozhraní .NET v systému, což může zahrnovat rozhraní API pro rozhraní Application Framework (například ASP.NET, WinForms). Pro cílové architektury založené na balíčku (například .NET Standard a .NET Core) jsou rozhraní API architektury definovaná balíčky nainstalovanými v aplikaci nebo knihovně. V takovém případě cílové rozhraní implicitně určuje balíček, který odkazuje na všechny balíčky, které dohromady tvoří rozhraní.

Viz [cílová rozhraní](frameworks.md).

## <a name="tfm"></a>TFM

Moniker cílového rozhraní .NET Framework.

Formát standardizovaného tokenu pro určení cílové architektury aplikace nebo knihovny .NET. Cílová rozhraní jsou obvykle odkazována krátkým názvem, například `net462` . Dlouhý tvar TFM (například. NETFramework, Version = 4.6.2) existuje, ale obecně se nepoužívá k určení cílové architektury.

Viz [cílová rozhraní](frameworks.md).

## <a name="uwp"></a>UWP

Univerzální platforma Windows.

Implementace .NET, která se používá k vytváření moderních, dotykové aplikace a softwaru Windows pro Internet věcí (IoT). Je navržený tak, aby sjednotí různé typy zařízení, na které můžete chtít cílit, včetně počítačů, tabletů, telefonů a i konzoly Xbox. UWP nabízí spoustu služeb, jako je centralizované úložiště aplikací, spouštěcí prostředí (kontejneru AppContainer) a sada rozhraní API systému Windows, které se mají použít místo Win32 (WinRT). Aplikace můžou být napsané v jazyce C++, C#, Visual Basic a JavaScriptu. Při použití C# a Visual Basic jsou rozhraní API .NET k dispozici v rozhraní .NET 5 (a .NET Core) a novějších verzích.

## <a name="see-also"></a>Viz také

- [Průvodce .NET](index.yml)
- [Průvodce .NET Framework](../framework/index.yml)
- [.NET Core](../core/index.yml)
- [ASP.NET – přehled](/aspnet/index#pivot=aspnet)
- [Přehled ASP.NET Core](/aspnet/index#pivot=core)
