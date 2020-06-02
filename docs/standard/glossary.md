---
title: Slovníček k technologii .NET
description: Zjistěte význam vybraných termínů používaných v dokumentaci .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 11ab0de4757a23c940ae04418a5a82ea79f71761
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287451"
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

Vysoce výkonná a open source implementace ASP.NET postavená na .NET Core pro více platforem.

Viz [dokumentace ASP.NET Core](/aspnet/#pivot=core).

## <a name="assembly"></a>sestavení

Soubor *. dll* / *. exe* , který může obsahovat kolekci rozhraní API, která mohou být volána aplikacemi nebo jinými sestaveními.

Sestavení může obsahovat typy, jako jsou rozhraní, třídy, struktury, výčty a Delegáti. Sestavení ve složce *bin* projektu jsou někdy označována jako *binární soubory*. Viz také [Knihovna](#library).

## <a name="clr"></a>CLR

Modul CLR (Common Language Runtime)

Přesný význam závisí na kontextu, ale modul CLR (Common Language Runtime) obvykle odkazuje na modul runtime .NET Framework. Modul CLR zpracovává přidělování a správu paměti. CLR je také virtuálním počítačem, který nespouští pouze aplikace, ale také generuje a kompiluje kód průběžně pomocí kompilátoru [JIT](#jit) . Aktuální implementace Microsoft CLR je jenom Windows.

## <a name="coreclr"></a>CoreCLR

Modul CLR (Common Language Runtime) .NET Core

Tento CLR je sestaven ze stejné základní znakové sady jako CLR. Původně CoreCLR byl modul runtime Silverlight a byl navržený tak, aby běžel na více platformách, konkrétně Windows a OS X. CoreCLR je teď součástí .NET Core a představuje zjednodušenou verzi CLR. Je to pořád modul runtime pro [více platforem](#cross-platform) , který teď zahrnuje podporu pro spoustu distribucí Linux. CoreCLR je také virtuální počítač s možnostmi JIT a spouštění kódu.

## <a name="corefx"></a>CoreFx

Základní knihovna tříd .NET Core (BCL)

> [!TIP]
> *FX* představuje *rozhraní*.

Sada knihoven, které tvoří systém. \* (a do omezeného rozsahu Microsoft. \* ) obsažené. BCL je pro obecné účely rozhraní nižší úrovně, které používá aplikační architektury vyšší úrovně, například ASP.NET Core, sestavení. Zdrojový kód .NET Core BCL je obsažen v [úložišti modulu runtime .NET Core](https://github.com/dotnet/runtime). Většina rozhraní API .NET Core je však také k dispozici v .NET Framework, takže si CoreFX můžete představit jako rozvětvení .NET Framework BCL.

## <a name="corert"></a>CoreRT

Modul runtime .NET Core.

Na rozdíl od CLR/CoreCLR není CoreRT virtuálním počítačem, což znamená, že nezahrnuje zařízení pro generování a spouštění kódu průběžně, protože nezahrnuje [JIT](#jit). Nicméně obsahuje [GC](#gc) a možnost identifikace typu za běhu (RTTI) a reflexe. Nicméně systém jeho typů je navržen tak, aby se metadata pro reflexi nevyžadovala. Nevyžadování metadat umožňuje mít řetěz nástrojů [AOT](#aot) , který může propojit nadbytečné metadata a (důležitější je) identifikovat kód, který aplikace nepoužívá. CoreRT je ve vývoji.

Přečtěte si [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).

## <a name="cross-platform"></a>pro různé platformy

Možnost vyvíjet a spouštět aplikaci, která se dá použít v několika různých operačních systémech, jako jsou Linux, Windows a iOS, aniž by se musely přepsat speciálně pro každé z nich. To umožňuje opakované použití kódu a konzistenci mezi aplikacemi na různých platformách.

## <a name="ecosystem"></a>ekosystému

Veškerý běhový software, vývojové nástroje a komunitní prostředky, které se používají k sestavování a spouštění aplikací pro danou technologii.

Pojem "ekosystém .NET" se od podobných termínů, jako je například .NET Stack, liší v zahrnutí aplikací a knihoven třetích stran. Tady je příklad ve větě:

- "Motivací za [.NET Standard](#net-standard) je vytvoření větší jednotnosti v ekosystému .NET."

## <a name="framework"></a>rozhraní

Obecně platí komplexní kolekce rozhraní API, která usnadňují vývoj a nasazování aplikací, které jsou založeny na konkrétní technologii. V tomto obecném smyslu jsou příklady aplikačních rozhraní ASP.NET Core a model Windows Forms. Viz také [Knihovna](#library).

Slovo "Framework" má konkrétnější technický význam v následujících termínech:

- [.NET Framework](#net-framework)
- [Cílová architektura](#target-framework)
- [TFM (moniker cílového rozhraní .NET Framework)](#tfm)

V existující dokumentaci "Framework" někdy odkazuje na [implementaci rozhraní .NET](#implementation-of-net). Například článek může volat rozhraní .NET Core do architektury. V této dokumentaci plánujeme toto matoucí využívání eliminovat.

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

- Jeden nebo více modulů runtime. Příklady: CLR, CoreCLR, CoreRT.
- Knihovna tříd, která implementuje verzi .NET Standard a může obsahovat další rozhraní API. Příklady: .NET Framework základní knihovny tříd, knihovna základních tříd .NET Core.
- Volitelně jeden nebo více aplikačních architektur. Příklady: ASP.NET, model Windows Forms a WPF jsou obsaženy v .NET Framework.
- Volitelně vývojové nástroje. Některé vývojové nástroje se sdílejí mezi více implementacemi.

Příklady implementací rozhraní .NET:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Univerzální platforma Windows (UPW)](#uwp)

## <a name="library"></a>knihovna

Kolekce rozhraní API, která mohou být volána aplikacemi nebo jinými knihovnami. Knihovna .NET se skládá z jednoho nebo více [sestavení](#assembly).

Slova Library a [Framework](#framework) se často používají jako synonyma.

## <a name="metapackage"></a>metapackage

Balíček NuGet, který nemá žádnou vlastní knihovnu, ale je jenom seznam závislostí. Zahrnuté balíčky mohou volitelně vytvořit rozhraní API pro cílovou architekturu.

Viz [balíčky, metabalíčky a architektury](../core/packages.md) .

## <a name="mono"></a>Mono

Mono je open source implementace .NET pro [různé platformy](#cross-platform) , která se používá hlavně v případě, že je potřeba malý modul runtime. Je to modul runtime, který vychází z aplikací Xamarin na zařízeních s Androidem, Mac, iOS, tvOS a watchOS a primárně se zaměřuje na aplikace, které vyžadují malé nároky.

Podporuje všechny aktuálně publikované verze .NET Standard.

V minulosti implementovala mono větší rozhraní API .NET Framework a emuluje některé z nejoblíbenějších funkcí v systému UNIX. Někdy se používá ke spouštění aplikací .NET, které spoléhají na tyto možnosti v systému UNIX.

Mono se obvykle používá s kompilátorem za běhu, ale také obsahuje úplný statický kompilátor (předem zkompilování), který se používá na platformách, jako je iOS.

Další informace o mono najdete v [dokumentaci k mono](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Termín pro [.NET Standard](#net-standard) a všechny implementace a úlohy [.NET](#implementation-of-net) . Vždy plně velkými písmeny, nikdy ".NET".

Projděte si [příručku .NET](index.yml)

## <a name="net-core"></a>.NET Core

Vysoce výkonná a open source implementace .NET pro více platforem. Zahrnuje základní modul CLR (Common Language Runtime) (CoreCLR), základní modul runtime AOT (CoreRT, ve vývoji), základní knihovnu základních tříd a základní sadu SDK.

Viz [.NET Core](../core/index.yml).

## <a name="net-core-cli"></a>Rozhraní příkazového řádku .NET Core

Sada nástrojů pro více platforem pro vývoj aplikací .NET Core.

Viz [.NET Core CLI](../core/tools/index.md).

## <a name="net-core-sdk"></a>Sada .NET Core SDK

Sada knihoven a nástrojů, které vývojářům umožňují vytvářet aplikace a knihovny .NET Core. Zahrnuje [.NET Core CLI](#net-core-cli) pro sestavování aplikací, knihoven .NET Core a modulu runtime pro vytváření a spouštění aplikací a spustitelný soubor dotnet (*dotnet. exe*), který spouští příkazy rozhraní příkazového řádku a spouští aplikace.

Další informace najdete v tématu [přehled .NET Core SDK](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Implementace rozhraní .NET, která běží pouze v systému Windows. Zahrnuje modul CLR (Common Language Runtime), knihovnu základních tříd a knihovny aplikačních architektur, jako jsou ASP.NET, model Windows Forms a WPF.

Viz [průvodce .NET Framework](../framework/index.yml).

## <a name="net-native"></a>.NET Native

Řetěz nástrojů kompilátoru, který vytváří nativní kód před časem (AOT), na rozdíl od JIT (just-in-time).

Kompilace probíhá na počítači vývojáře podobně jako kompilátor jazyka C++ a linker funguje. Odebírá nepoužitý kód a stráví více času optimalizací. Extrahuje kód z knihoven a sloučí je do spustitelného souboru. Výsledkem je jeden modul, který představuje celou aplikaci.

UWP byla první aplikační architektura, kterou .NET Native podporuje. Nyní podporujeme vytváření nativních konzolových aplikací pro Windows, macOS a Linux.

Viz [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET Standard

Formální specifikace rozhraní .NET API, které jsou k dispozici v každé implementaci rozhraní .NET.

Specifikace .NET Standard se v dokumentaci někdy označuje jako knihovna. Vzhledem k tomu, že knihovna obsahuje implementace rozhraní API, nikoli pouze specifikace (rozhraní), je pro volání .NET Standard "Library" zavádějící. V této dokumentaci plánujeme toto použití eliminovat, s výjimkou odkazu na název .NET Standard Metapackage ( `NETStandard.Library` ).

Viz [.NET Standard](net-standard.md).

## <a name="ngen"></a>NGEN

Generování nativních (imagí)

Tuto technologii si můžete představit jako trvalý kompilátor JIT. Obvykle kompiluje kód na počítači, kde je spuštěn kód, ale kompilace obvykle probíhá v době instalace.

## <a name="package"></a>balíček

Balíček NuGet &mdash; nebo pouze balíček &mdash; je soubor *. zip* s jedním nebo více sestaveními se stejným názvem společně s dalšími metadaty, jako je jméno autora.

Soubor *. zip* má příponu *. nupkg* a může obsahovat prostředky, jako jsou soubory *DLL* a *XML* soubory pro použití s více cílovými rozhraními a verzemi. Při instalaci v aplikaci nebo knihovně jsou příslušné prostředky vybrány na základě cílového rozhraní určeného aplikací nebo knihovnou. Prostředky, které definují rozhraní, jsou ve složce *ref* a assety definující implementaci jsou ve složce *lib* .

## <a name="platform"></a>platforma

Operační systém a hardware, na kterém běží, jako je Windows, macOS, Linux, iOS a Android.

Tady jsou příklady použití ve větách:

- ".NET Core je implementace .NET pro různé platformy."
- "Profily PCL reprezentují platformy Microsoft, zatímco .NET Standard nezávislá na platformu."

Dokumentace rozhraní .NET často používá "platformu .NET", která znamená implementaci .NET nebo .NET Stack včetně všech implementací. Obě tato použití se z tohoto hlediska snaží obměňujte s primárním (operačním nebo hardwarovým) významem, takže plánujeme tato použití z dokumentace eliminovat.

## <a name="runtime"></a>modul runtime

Spouštěcí prostředí pro spravovaný program.

Operační systém je součástí běhového prostředí, ale není součástí modulu .NET Runtime. Tady je několik příkladů prostředí .NET Runtime:

- Common Language Runtime (CLR)
- Core Common Language Runtime (CoreCLR)
- .NET Native (pro UWP)
- Mono runtime

Dokumentace rozhraní .NET někdy používá "runtime", což znamená implementaci rozhraní .NET. Například v následujících větách "runtime" by se měla nahradit výrazem "implementace":

- "Různé moduly runtime .NET implementují konkrétní verze .NET Standard."
- "Knihovny určené ke spuštění na více modulech runtime by měly cílit na toto rozhraní." (odkazování na .NET Standard)
- "Různé moduly runtime .NET implementují konkrétní verze .NET Standard. … Každá verze modulu .NET runtime inzeruje nejvyšší .NET Standard verzi, kterou podporuje...

Plánujeme toto nekonzistentní použití eliminovat.

## <a name="stack"></a>stack

Sada programovacích technologií používaných společně k sestavování a spouštění aplikací.

Rozhraní .NET Stack odkazuje na .NET Standard a všechny implementace rozhraní .NET. Fráze ".NET Stack" může odkazovat na jednu implementaci rozhraní .NET.

## <a name="target-framework"></a>Cílová architektura

Kolekce rozhraní API, na kterých závisí aplikace .NET nebo knihovna

Aplikace nebo knihovna může cílit na verzi .NET Standard (například .NET Standard 2,0), což je specifikace pro standardizovanou sadu rozhraní API napříč všemi implementacemi .NET. Aplikace nebo knihovna může také cílit na verzi konkrétní implementace rozhraní .NET. v takovém případě získá přístup k rozhraním API pro konkrétní implementaci. Například aplikace, která se zaměřuje na Xamarin. iOS, získá přístup k obálkám rozhraní API iOS poskytovaných v Xamarin.

Pro některé cílové architektury (například .NET Framework) jsou dostupná rozhraní API definovaná sestaveními, která implementuje implementace rozhraní .NET v systému, což může zahrnovat rozhraní API pro rozhraní Application Framework (například ASP.NET, WinForms). Pro cílové architektury založené na balíčku (například .NET Standard a .NET Core) jsou rozhraní API architektury definovaná balíčky nainstalovanými v aplikaci nebo knihovně. V takovém případě cílové rozhraní implicitně určuje Metapackage, který odkazuje na všechny balíčky, které dohromady tvoří rozhraní.

Viz [cílová rozhraní](frameworks.md).

## <a name="tfm"></a>TFM

Moniker cílového rozhraní .NET Framework.

Formát standardizovaného tokenu pro určení cílové architektury aplikace nebo knihovny .NET. Cílová rozhraní jsou obvykle odkazována krátkým názvem, například `net462` . Dlouhý tvar TFM (například. NETFramework, Version = 4.6.2) existuje, ale obecně se nepoužívá k určení cílové architektury.

Viz [cílová rozhraní](frameworks.md).

## <a name="uwp"></a>UPW

Univerzální platforma Windows.

Implementace .NET, která se používá k vytváření moderních, dotykové aplikace a softwaru Windows pro Internet věcí (IoT). Je navržený tak, aby sjednotí různé typy zařízení, na které můžete chtít cílit, včetně počítačů, tabletů, telefonů a i konzoly Xbox. UWP nabízí spoustu služeb, jako je centralizované úložiště aplikací, spouštěcí prostředí (kontejneru AppContainer) a sada rozhraní API systému Windows, které se mají použít místo Win32 (WinRT). Aplikace můžou být napsané v jazyce C++, C#, Visual Basic a JavaScriptu. Při použití C# a Visual Basic rozhraní API .NET poskytuje .NET Core.

## <a name="see-also"></a>Viz také

- [Průvodce .NET](index.yml)
- [Průvodce .NET Framework](../framework/index.yml)
- [.NET Core](../core/index.yml)
- [ASP.NET – přehled](/aspnet/index#pivot=aspnet)
- [Přehled ASP.NET Core](/aspnet/index#pivot=core)
