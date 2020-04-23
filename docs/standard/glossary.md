---
title: Slovníček k technologii .NET
description: Zjistěte význam vybraných termínů použitých v dokumentaci k rozhraní .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: e7608ee7e68300d691df51aed923db0e8b518165
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102473"
---
# <a name="net-glossary"></a>Slovníček k technologii .NET

Primárním cílem tohoto glosáře je objasnit významy vybraných termínů a akronymů, které se často objevují v dokumentaci .NET bez definic.

## <a name="aot"></a>AOT

Překladač dopředu.

Podobně jako [JIT](#jit), tento kompilátor také překládá [IL](#il) na strojový kód. Na rozdíl od kompilace JIT kompilace AOT se stane před spuštěním aplikace a obvykle se provádí na jiném počítači. Vzhledem k tomu, že řetězce nástrojů AOT nekompilují za běhu, nemusí minimalizovat čas strávený kompilací. To znamená, že mohou trávit více času optimalizací. Vzhledem k tomu, že kontext AOT je celá aplikace, kompilátor AOT také provádí propojení mezi moduly a analýzu celého programu, což znamená, že jsou dodržovány všechny odkazy a je vytvořen jeden spustitelný soubor.

Viz [CoreRT](#corert) a [.NET Native](#net-native).

## <a name="aspnet"></a>ASP.NET

Původní ASP.NET implementaci, která je dodávána s rozhraním .NET Framework.

Někdy je ASP.NET zastřešující termín, který odkazuje na obě ASP.NET implementace, včetně ASP.NET Core. Význam, který termín nese v dané instanci je určena kontextu. Odkazovat na ASP.NET 4.x, pokud chcete, aby bylo jasné, že nepoužíváte ASP.NET znamená obě implementace.

Viz [dokumentace k ASP.NET](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Multiplatformní, vysoce výkonná implementace ASP.NET s otevřeným zdrojovým kódem postavená na jádru .NET Core.

Viz [dokumentace ASP.NET Core](/aspnet/#pivot=core).

## <a name="assembly"></a>sestavení

Soubor *.dll.exe,*/*.exe* který může obsahovat kolekci souborů API, která mohou být volána aplikacemi nebo jinými sestaveními.

Sestavení může obsahovat typy, jako jsou rozhraní, třídy, struktury, výčty a delegáty. Sestavení ve složce *přihrádky* projektu jsou někdy *označovány*jako binární soubory . Viz také [knihovna](#library).

## <a name="clr"></a>CLR

Běžný jazyk Runtime.

Přesný význam závisí na kontextu, ale common language runtime obvykle odkazuje na runtime rozhraní .NET Framework. CLR zpracovává přidělení paměti a správu. CLR je také virtuální počítač, který nejen spouští aplikace, ale také generuje a kompiluje kód průběžně pomocí kompilátoru [JIT.](#jit) Aktuální implementace Microsoft CLR je pouze systém Windows.

## <a name="coreclr"></a>CoreCLR

.NET Core Common Language Runtime.

Tento CLR je sestaven ze stejného základu kódu jako CLR. Původně byl CoreCLR runtime programu Silverlight a byl navržen tak, aby běžel na více platformách, konkrétně na platformách Windows a OS X. CoreCLR je nyní součástí .NET Core a představuje zjednodušenou verzi CLR. Je to stále [runtime napříč](#cross-platform) platformami, nyní včetně podpory mnoha distribucí Linuxu. CoreCLR je také virtuální počítač s možnostmi JIT a spuštění kódu.

## <a name="corefx"></a>CoreFx

Knihovna základních tříd .NET Core (BCL)

> [!TIP]
> *Fx* je zkratka pro *rámec*.

Sada knihoven, které tvoří systém. \* (a v omezené míře\*Microsoft.) obory názvů. BCL je obecný účel, nižší úroveň rámce, které vyšší úrovně aplikační architektury, jako je například ASP.NET Core, stavět na. Zdrojový kód souboru .NET Core BCL je obsažen v [úložišti runtime .NET Core](https://github.com/dotnet/runtime). Většina rozhraní API .NET Core jsou však k dispozici také v rozhraní .NET Framework, takže si můžete myslet CoreFX jako rozsvázu rozhraní .NET Framework BCL.

## <a name="corert"></a>CoreRT

Běhový čas jádra .NET.

Na rozdíl od CLR/CoreCLR, CoreRT není virtuální stroj, což znamená, že nezahrnuje zařízení pro generování a spouštění kódu on-the-fly, protože neobsahuje [JIT](#jit). Zahrnuje však [GC](#gc) a schopnost identifikace typu běhu (RTTI) a reflexe. Jeho typ systému je však navržen tak, aby metadata pro reflexi není vyžadována. Nevyžadování metadat umožňuje mít řetězec nástrojů [AOT,](#aot) který může propojit nadbytečná metadata a (což je důležitější) identifikovat kód, který aplikace nepoužívá. CoreRT je ve vývoji.

Viz [Úvod do .NET Nativní a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).

## <a name="cross-platform"></a>pro různé platformy

Schopnost vyvíjet a spouštět aplikaci, která může být použita na více různých operačních systémech, jako je Linux, Windows a iOS, aniž by bylo třeba přepisovat konkrétně pro každý z nich. To umožňuje opětovné použití kódu a konzistence mezi aplikacemi na různých platformách.

## <a name="ecosystem"></a>Ekosystému

Veškerý runtime software, vývojové nástroje a komunitní prostředky, které se používají k vytváření a spouštění aplikací pro danou technologii.

Termín ".NET ekosystém" se liší od podobných termínů, jako je například "zásobník.NET" v jeho začlenění aplikací a knihoven třetích stran. Zde je příklad ve větě:

- "Motivací [standardu .NET](#net-standard) standard je vytvořit větší jednotnost v ekosystému .NET."

## <a name="framework"></a>rozhraní

Obecně platí, že komplexní kolekce api, která usnadňuje vývoj a nasazení aplikací, které jsou založeny na konkrétní technologii. V tomto obecném smyslu jsou ASP.NET Core a Windows Forms příklady aplikačních architektur. Viz také [knihovna](#library).

Slovo "rámec" má konkrétnější technický význam v následujících pojmech:

- [.NET Framework](#net-framework)
- [cílový rámec](#target-framework)
- [TFM (zástupný název cílového rámce)](#tfm)

Ve stávající dokumentaci "framework" někdy odkazuje na [implementaci rozhraní .NET](#implementation-of-net). Například článek může volat .NET Core rámec. Plánujeme odstranit toto matoucí použití z dokumentace.

## <a name="gc"></a>Uvolňování paměti

Popelář.

Systém uvolňování paměti je implementací automatické správy paměti.  Gc uvolní paměť obsazenou objekty, které se již nepoužívají.

Viz [Uvolňování paměti](garbage-collection/index.md).

## <a name="il"></a>IL

Zprostředkující jazyk.

Jazyky .NET vyšší úrovně, například C#, se kompilují do sady instrukcí bez hardwaru, která se nazývá Zprostředkující jazyk (IL). IL se někdy označuje jako MSIL (Microsoft IL) nebo CIL (Common IL).

## <a name="jit"></a>JIT

Kompilátor just-in-time.

Podobně jako [AOT](#aot), tento kompilátor překládá [IL](#il) na strojový kód, který procesor chápe. Na rozdíl od AOT kompilace JIT se provádí na vyžádání a provádí se na stejném počítači, který kód potřebuje ke spuštění. Vzhledem k tomu, že kompilace JIT dochází během provádění aplikace, čas kompilace je součástí běhu. Kompilátory JIT tedy musí vyvážit čas strávený optimalizací kódu proti úsporám, které může výsledný kód vytvořit. Ale JIT zná skutečný hardware a může osvobodit vývojáře od nutnosti doručovat různé implementace.

## <a name="implementation-of-net"></a>implementace rozhraní .NET

Implementace rozhraní .NET zahrnuje:

- Jeden nebo více runtimes. Příklady: CLR, CoreCLR, CoreRT.
- Knihovna tříd, která implementuje verzi standardu .NET a může obsahovat další rozhraní API. Příklady: .NET Framework Base Class Library, .NET Core Base Class Library.
- Volitelně jeden nebo více rozhraní aplikace. Příklady: ASP.NET, Windows Forms a WPF jsou zahrnuty v rozhraní .NET Framework.
- Volitelně, vývojové nástroje. Některé vývojové nástroje jsou sdíleny mezi více implementací.

Příklady implementací rozhraní .NET:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Univerzální platforma Windows (UPW)](#uwp)

## <a name="library"></a>knihovna

Kolekce api, která mohou být volána aplikacemi nebo jinými knihovnami. Knihovna .NET se skládá z jednoho nebo více [sestavení](#assembly).

Slova knihovna a [rámec](#framework) jsou často používány synonymně.

## <a name="metapackage"></a>Metabalíček

Balíček NuGet, který nemá vlastní knihovnu, ale je pouze seznam závislostí. Zahrnuté balíčky můžete volitelně vytvořit rozhraní API pro cílové rozhraní.

Viz [Balíčky, metabalíčky a rámce](../core/packages.md)

## <a name="mono"></a>Mono

Mono je implementace open [source, cross-platform](#cross-platform) .NET, která se používá hlavně v případě, že je vyžadován malý runtime. Je to runtime, který pohání aplikace Xamarin v systémech Android, Mac, iOS, tvOS a watchOS a je zaměřen především na aplikace, které vyžadují malé rozměry.

Podporuje všechny aktuálně publikované verze .NET Standard.

Mono historicky implementoval větší API rozhraní .NET Framework a emuloval některé z nejpopulárnějších schopností na Unixu. Někdy se používá ke spuštění aplikací .NET, které jsou závislé na těchto funkcích na Unixu.

Mono se obvykle používá s kompilátorem just-in-time, ale obsahuje také úplný statický kompilátor (kompilace dopředu času), který se používá na platformách, jako je iOS.

Další informace o mono, naleznete [v dokumentaci Mono](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Zastřešující termín pro [standard .NET](#net-standard) a všechny implementace a [úlohy .NET.](#implementation-of-net) Vždy plně kapitalizovaný, nikdy ".Net".

Podívejte se na [průvodce .NET](index.yml)

## <a name="net-core"></a>.NET Core

Implementace rozhraní .NET s otevřeným zdrojovým kódem napříč platformami a vysokým výkonem. Zahrnuje základní běžný jazyk Runtime (CoreCLR), core AOT Runtime (CoreRT, ve vývoji), základní základní třídy knihovny a základní sdk.

Viz [jádro .NET](../core/index.yml).

## <a name="net-core-cli"></a>Rozhraní příkazového řádku .NET Core

Řetězec nástrojů pro různé platformy pro vývoj aplikací .NET Core.

Viz [rozhraní CLI jádra .NET](../core/tools/index.md).

## <a name="net-core-sdk"></a>Sada .NET Core SDK

Sada knihoven a nástrojů, které vývojářům umožňují vytvářet základní aplikace a knihovny .NET. Zahrnuje [rozhraní příkazového příkazu .NET Core](#net-core-cli) pro vytváření aplikací, knihovny .NET Core a modul runtime pro vytváření a spouštění aplikací a spustitelný soubor dotnet (*dotnet.exe),* který spouští příkazy příkazového příkazu příkazového příkazu a spouští aplikace.

Viz [přehled sady .NET Core SDK](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Implementace rozhraní .NET, která běží pouze v systému Windows. Zahrnuje clr (Common Language Runtime), knihovnu základních tříd a knihovny architektury aplikací, jako jsou ASP.NET, Windows Forms a WPF.

Viz [Průvodce architekturou .NET](../framework/index.yml).

## <a name="net-native"></a>.NET Native

Řetěz kompilátoru nástroje, který vytváří nativní kód dopředu na čas (AOT), na rozdíl od just-in-time (JIT).

Kompilace se děje na počítači vývojáře podobné způsobu, jakým funguje kompilátor jazyka C++ a propojovací program. Odebere nepoužívaný kód a stráví více času optimalizací. Extrahuje kód z knihoven a slučuje je do spustitelného souboru. Výsledkem je jeden modul, který představuje celou aplikaci.

UPW byl první aplikační rámec podporovaný .NET Native. Nyní podporujeme vytváření nativních konzolových aplikací pro Windows, macOS a Linux.

Viz [Úvod do .NET Nativní a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET Standard

Formální specifikace rozhraní API .NET, které jsou k dispozici v každé implementaci rozhraní .NET.

Specifikace standardu .NET se někdy nazývá knihovna v dokumentaci. Vzhledem k tomu, že knihovna obsahuje implementace rozhraní API, nikoli pouze specifikace (rozhraní), je zavádějící volat .NET Standard jako "knihovnu". Toto použití plánujeme vyloučit z dokumentace, s výjimkou odkazu na název`NETStandard.Library`metabalíčku .NET Standard ( ).

Viz [standard .NET](net-standard.md).

## <a name="ngen"></a>Ngen

Nativní (image) generace.

Tuto technologii si můžete myslet jako trvalý kompilátor JIT. Obvykle zkompiluje kód na počítači, kde je kód spuštěn, ale kompilace obvykle dochází v době instalace.

## <a name="package"></a>Balíček

Balíček &mdash; NuGet nebo &mdash; pouze balíček je *soubor ZIP* s jedním nebo více sestaveními se stejným názvem spolu s dalšími metadaty, jako je například jméno autora.

Soubor *ZIP* má příponu *.nupkg* a může obsahovat datové zdroje, například soubory *DLL* a *soubory XML,* pro použití s více cílovými rozhraními a verzemi. Při instalaci v aplikaci nebo knihovně jsou příslušné datové zdroje vybrány na základě cílového rozhraní určeného aplikací nebo knihovnou. Datové zdroje, které definují rozhraní, jsou ve složce *ref* a datové zdroje, které definují implementaci, jsou ve složce *lib.*

## <a name="platform"></a>platforma

Operační systém a hardware, na kterých běží, jako jsou Windows, macOS, Linux, iOS a Android.

Zde jsou příklady použití ve větách:

- ".NET Core je implementace napříč platformami rozhraní .NET."
- "PcL profily představují platformy společnosti Microsoft, zatímco standard .NET je agnostik na platformě."

Dokumentace .NET často používá ".NET platforma" znamenat buď implementaci .NET nebo zásobníku .NET včetně všech implementací. Obě tato použití mají tendenci se zaměňovat s primárním (OS / hardware), takže plánujeme odstranit tato použití z dokumentace.

## <a name="runtime"></a>modul runtime

Prostředí spuštění spravovaného programu.

Operační systém je součástí runtime prostředí, ale není součástí běhu .NET. Zde jsou některé příklady runtimes rozhraní .NET:

- Common Language Runtime (CLR)
- Základní běžný jazyk Runtime (CoreCLR)
- .NET Nativní (pro UPW)
- Mono runtime

Dokumentace .NET někdy používá "runtime" znamenat implementaci .NET. Například v následujícívěti "runtime" by měl být nahrazen "implementace":

- "Různé runtimes rozhraní .NET implementují konkrétní verze standardu .NET).
- "Knihovny, které jsou určeny ke spuštění na více runtimes by měl cílit na tento rámec." (s odkazem na standard .NET)
- "Různé runtimes rozhraní .NET implementují konkrétní verze standardu .NET. … Každá verze runtime rozhraní .NET inzeruje nejvyšší verzi .NET Standard, kterou podporuje ..."

Plánujeme eliminovat toto nekonzistentní použití.

## <a name="stack"></a>stack

Sada programovacích technologií, které se používají společně k vytváření a spouštění aplikací.

"Zásobník rozhraní .NET" odkazuje na standard .NET a všechny implementace rozhraní .NET. Frázi "zásobník .NET" může odkazovat na jednu implementaci rozhraní .NET.

## <a name="target-framework"></a>cílový rámec

Kolekce rozhraní API, na které závisí aplikace nebo knihovna .NET.

Aplikace nebo knihovna může cílit na verzi rozhraní .NET Standard (například .NET Standard 2.0), což je specifikace pro standardizovanou sadu rozhraní API ve všech implementacích rozhraní .NET. Aplikace nebo knihovna může také cílit na verzi konkrétní implementace rozhraní .NET, v takovém případě získá přístup k rozhraním API specifické pro implementaci. Například aplikace, která cílí na Xamarin.iOS získá přístup k obálky rozhraní API poskytované Xamarin.

Pro některé cílové architektury (například rozhraní .NET Framework) jsou dostupná rozhraní API definována sestaveními, která implementace .NET nainstaluje do systému, což může zahrnovat rozhraní API rozhraní API rozhraní ap (například ASP.NET, WinForms). Pro cílové architektury založené na balíčcích (například .NET Standard a .NET Core) jsou rozhraní API architektury definována balíčky nainstalovanými v aplikaci nebo knihovně. V takovém případě cílový rámec implicitně určuje metabalíček, který odkazuje na všechny balíčky, které společně tvoří rámec.

Viz [Cílové rámce](frameworks.md).

## <a name="tfm"></a>Tfm

Zástupný název rozhraní target.

Standardizovaný formát tokenu pro určení cílového rozhraní aplikace nebo knihovny .NET. Cílové architektury jsou obvykle odkazovány krátkým názvem, například `net462`. Dlouhodobé TFM (například . NETFramework,Version=4.6.2) existují, ale obecně se nepoužívají k určení cílového rozhraní.

Viz [Cílové rámce](frameworks.md).

## <a name="uwp"></a>UWP

Univerzální platforma Windows.

Implementace rozhraní .NET, která se používá pro vytváření moderních aplikací a softwaru systému Windows s podporou dotykového ovládání pro Internet věcí (IoT). Je navržen tak, aby sjednocovat různé typy zařízení, které můžete chtít cílit, včetně počítačů, tabletů, telefonů, a dokonce i Xbox. Upwp poskytuje mnoho služeb, jako je například centralizované úložiště aplikací, spuštění prostředí (AppContainer) a sadu windows API pro použití namísto Win32 (WinRT). Aplikace lze psát v jazycích C++, C#, Visual Basic a JavaScript. Při použití jazyka C# a jazyka Visual Basic jsou rozhraní API .NET poskytována rozhraním .NET Core.

## <a name="see-also"></a>Viz také

- [Průvodce rozhraním .NET](index.yml)
- [Průvodce rámcem rozhraní .NET](../framework/index.yml)
- [.NET Core](../core/index.yml)
- [přehled ASP.NET](/aspnet/index#pivot=aspnet)
- [ASP.NET základní přehled](/aspnet/index#pivot=core)
