---
title: .NET – Glosář
description: Přečtěte si významu vybraných termínů používaných v dokumentaci k rozhraní .NET.
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 4ffcf56ba171192048a736b58ddcfa591fd3af58
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580846"
---
# <a name="net-glossary"></a>.NET – Glosář

Hlavním cílem tento glosář je objasnit význam vybrané podmínky a zkratky, které se často zobrazují v dokumentaci k .NET bez definic.

## <a name="aot"></a>AOT

Kompilátor ahead of time.

Podobně jako [JIT](#jit), tento kompilátor se také přeloží [IL](#il) do strojového kódu. Na rozdíl od kompilace JIT kompilace AOT se stane, než aplikace spouští a se obvykle provádí v jiném počítači. Protože řetězce nástrojů AOT není kompilaci za běhu, nemají minimalizovat čas strávený kompilaci. To znamená, že může věnovat víc času optimalizace. Protože kontextu AOT celé aplikace, provádí kompilátor AOT také propojení mezi moduly a analýzu celého programu, což znamená, že jsou všechny odkazy a a je vytvořen jeden spustitelný soubor.

## <a name="aspnet"></a>ASP.NET 

Původní implementace technologie ASP.NET, která se dodává s rozhraním .NET Framework.

Někdy je technologie ASP.NET se o zastřešující pojem, který odkazuje na obou implementacích technologie ASP.NET, včetně ASP.NET Core. Význam, který představuje výraz v jakékoli dané instance se určuje podle kontextu. Odkazovat na technologii ASP.NET 4.x, pokud chcete, aby bylo jasné, které nejsou pomocí technologie ASP.NET k označení obou implementacích. 

Zobrazit [dokumentace k ASP.NET](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Platformově univerzální, vysoce výkonná open source implementace technologie ASP.NET založená na rozhraní .NET Core.

Zobrazit [dokumentace k ASP.NET Core](/aspnet/#pivot=core).

## <a name="assembly"></a>sestavení

A *.dll*/*.exe* soubor, který může obsahovat sadu rozhraní API, která mohou být volány aplikací nebo jiná sestavení.

Sestavení může obsahovat typy, jako jsou rozhraní, třídy, struktury, výčty a delegáti. Sestavení v projektu *bin* složky jsou někdy označovány jako *binární soubory*. Viz také [knihovny](#library).

## <a name="clr"></a>CLR

Modul Common Language Runtime.

Přesné význam závisí na kontextu, ale to se obvykle odkazuje na modul runtime rozhraní .NET Framework. Modul CLR zpracovává přidělení paměti a správu. Modul CLR je také virtuální počítač, který nejen spustí aplikace, ale také generuje a kompilaci kódu pomocí na průběžné [JIT](#jit) kompilátoru. Aktuální implementace Microsoft CLR je jenom pro Windows.

## <a name="coreclr"></a>CoreCLR

.NET core CLR.

Tato CLR je sestaven z základní jako CLR stejný kód. Původně CoreCLR byl modul runtime technologie Silverlight a byl navržen pro spouštění na více platforem, konkrétně Windows a OS X. CoreCLR je teď součástí sady .NET Core a představuje zjednodušenou verzi modulu CLR. Stále [multiplatformní](#cross-platform) modulu runtime, nyní včetně podpory pro řadu distribucí systému Linux. CoreCLR je také virtuální počítač s možností spouštění JIT a kód.

## <a name="corefx"></a>CoreFX

Knihovna základních tříd .NET core (BCL)

Oborech názvů sadu knihoven, které tvoří System.* (a do jisté míry oborů Microsoft.*). Obecné rozhraní framework nižší úrovně, která vycházejí vyšší úrovně aplikačních architektur, jako je ASP.NET Core, je BCL. Zdrojový kód .NET Core BCL je součástí [CoreFX úložiště](https://github.com/dotnet/corefx). Většina rozhraní API .NET Core jsou však také k dispozici v rozhraní .NET Framework, tak CoreFX si můžete představit jako fork BCL rozhraní .NET Framework.

## <a name="corert"></a>CoreRT

Modul runtime .NET core.

Na rozdíl od CLR/CoreCLR, CoreRT není virtuální počítač, což znamená, že neobsahuje funkce pro generování a spuštění kódu v běhu, protože neobsahuje [JIT](#jit). , Ale patří [GC](#gc) a možnost identifikace typu modulu runtime (RTTI) a reflexe. Ale jeho typ systému je navržený tak, aby metadata pro účely reflexe není povinné. Díky tomu máte [AOT](#aot) nástroj řetězec, který můžete propojit tokeny nadbytečný metadat a (důležitější) identifikovat kód, který se aplikace nepoužívá. CoreRT je ve vývoji.

Zobrazit [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="cross-platform"></a>pro různé platformy

Možnost vyvíjet a spouštět aplikace, která je možné v několika různých operačních systémech, jako je Linux, Windows a iOS, aniž byste museli znovu napsat speciálně pro každý z nich. Díky tomu opakovanému použití kódu a konzistenci mezi aplikací na různých platformách.

## <a name="ecosystem"></a>Ekosystém

Všechny softwarové modulu runtime, vývojové nástroje a komunitní zdroje, které se používají k vytváření a spouštění aplikací pro dané technologii.

Termín "Ekosystému .NET" se liší od podobných podmínek, jako je například "Zásobník .NET" v jeho zařazení aplikace třetích stran a knihoven. Tady je příklad ve větě:

- "Motivace za [.NET Standard](#net-standard) navázat větší sjednocení v ekosystému .NET." 

## <a name="framework"></a>rozhraní

Obecně platí komplexní kolekce rozhraní API, který usnadňuje vývoj a nasazování aplikací, které jsou založeny na konkrétní technologii. V tomto obecném smyslu tento pojem ASP.NET Core a Windows Forms jsou příkladem aplikačních architektur. Viz také [knihovny](#library).

Slovo "rozhraní" má konkrétnější technické význam v následující podmínky:
* [.NET Framework](#net-framework)
* [Cílová architektura](#target-framework)
* [TFM (moniker cílového rozhraní framework)](#tfm)

Ve stávající dokumentaci "rozhraní" někdy odkazuje [implementace .NET](#implementation-of-net). Článek například může volat .NET Core rozhraní. Plánujeme, chcete-li odstranit tento matoucí využití v dokumentaci ke službě.

## <a name="gc"></a>Uvolňování paměti

Systém uvolňování paměti.

Uvolňování paměti je implementace Automatická správa paměti.  Uvolňování paměti uvolní paměť obsazena objekty, které jsou už používá. 

Zobrazit [uvolňování](garbage-collection/index.md).

## <a name="il"></a>IL

Převodní jazyk.

Vyšší úrovně jazyků .NET, jako je C#, kompilovat dolů sada instrukcí nezávislá na hardwaru, která se nazývá Intermediate Language (IL). IL se někdy označuje jako jazyk MSIL (Microsoft IL) nebo soubor CIL (Common IL).

## <a name="jit"></a>JIT

Kompilátor Just-in-time.

Podobně jako [AOT](#aot), tento kompilátor překládá [IL](#il) do strojového kódu, která analyzuje procesoru. Na rozdíl od kompilaci AOT kompilace JIT se stane, na vyžádání a provádí ve stejném počítači, který je potřeba spouštět kód. Vzhledem k tomu, že během provádění dojde k JIT kompilaci, kompilace je součástí čas spuštění. Kompilátory JIT tedy mít vyvážit dobu strávenou optimalizace kódu proti úspory, které mohou způsobit výsledný kód. Ale zná skutečné hardwarové JIT a můžete uvolnit vývojáře od přitom nutné dodávat jedná o rozdílné implementace.

## <a name="implementation-of-net"></a>implementace rozhraní .NET

Implementace .NET zahrnuje následující položky:

- Jeden nebo více modulů runtime. Příklady: CoreRT CLR, CoreCLR.
- Knihovna tříd, který implementuje na verzi .NET Standard a může taky obsahovat další rozhraní API. Příklady: Základní knihovny tříd .NET Framework, knihovně základních tříd .NET Core.
- Volitelně můžete jeden nebo více aplikačních architektur. Příklady: ASP.NET, Windows Forms a WPF jsou zahrnuty v rozhraní .NET Framework.
- Volitelně můžete nástroje pro vývoj. Některé vývojové nástroje jsou sdíleny více implementací.

Příklady implementace .NET:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Univerzální platforma Windows (UPW)](#uwp)

## <a name="library"></a>knihovna

Kolekce rozhraní API, která mohou být volány aplikací nebo jiné knihovny. Knihovna .NET se skládá z jedné nebo více [sestavení](#assembly).

Knihovna slova a [framework](#framework) se často používají jako synonyma.

## <a name="metapackage"></a>Microsoft.aspnetcore.all

Balíček NuGet, který nemá žádná knihovna samostatně, ale je pouze seznam závislostí. Na zahrnuté balíčky můžete volitelně vytvořit rozhraní API pro cílovou architekturu.

Zobrazit [balíčky, Metabalíčky a architektury](../core/packages.md)

## <a name="mono"></a>Mono

Mono je open source [multiplatformní](#cross-platform) implementace .NET, který se používá hlavně při malý modul runtime je povinný. Je modul runtime, který zajišťuje provoz aplikací v Xamarinu na Android, Mac, iOS, tvOS a watchOS a se zaměřuje především na aplikace, které vyžadují malé náklady.

Podporuje všechny aktuálně publikované verze .NET Standard.

V minulosti Mono implementovaná větší API rozhraní .NET Framework a emulované některé z nejoblíbenějších funkcí v systému Unix. Někdy se používá ke spouštění aplikací .NET, které využívají tyto funkce v systému Unix.

Mono se obvykle používá s kompilátorem za běhu, ale obsahuje taky celý statický kompilátor (ahead of time kompilace), který se používá na platformách, jako je iOS.

Další informace o Mono, najdete v článku [dokumentace Mono](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Zastřešující pojem pro [.NET Standard](#net-standard) a všechny [implementace .NET](#implementation-of-net) a úlohy. Vždy velkými písmeny, nikdy ".Net".

Zobrazit [Průvodce technologií .NET](index.md)

## <a name="net-core"></a>.NET Core 

Napříč platformami, vysoce výkonná open source implementace .NET. Zahrnuje základní Common Language Runtime (CoreCLR), Core Runtime AOT (ve vývoji CoreRT), základní knihovny tříd Base a Core SDK.

Zobrazit [.NET Core](../core/index.md).

## <a name="net-core-cli"></a>.NET core CLI

Multiplatformní sadu nástrojů pro vývoj aplikací .NET Core.

Zobrazit [nástroje rozhraní příkazového řádku (CLI) pro .NET Core](../core/tools/index.md).

## <a name="net-core-sdk"></a>.NET core SDK

Sada knihovny a nástroje, které umožňují vývojářům vytvářet aplikace .NET Core a knihovny. Zahrnuje [rozhraní příkazového řádku .NET Core](#net-core-cli) pro vývoj aplikací, knihoven .NET Core a modul runtime pro sestavování a spouštění aplikací a dotnet spustitelný soubor (*dotnet.exe*), který spouští příkazy rozhraní příkazového řádku a spuštění aplikace.

Zobrazit [Přehled sady SDK .NET Core](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Implementace rozhraní .NET, na kterém běží pouze na Windows. Zahrnuje Common Language Runtime (CLR), základní knihovny tříd a rozhraní framework knihovny aplikací, jako je ASP.NET, Windows Forms a WPF.

Zobrazit [rozhraní .NET Framework – průvodce](../framework/index.md).

## <a name="net-native"></a>.NET Native

Řetěz kompilátoru nástroj, který vytváří nativní kód ahead-of-time (AOT), na rozdíl od just-in-time (JIT).

Probíhá kompilace na počítači pro vývojáře podobným způsobem, jakým C++ kompilátor a propojovací program funguje. Odebere nevyužité kódu a tráví víc času na jeho optimalizace. Extrahuje z knihovny kódu a sloučí je do spustitelného souboru. Výsledkem je jeden modul, který představuje celé aplikace.

UPW se první aplikační platformu .NET Native nepodporují. Nyní podporujeme sestavování nativních konzolové aplikace pro Windows, macOS a Linux.

Zobrazit [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET standard

Formální specifikaci rozhraní API pro .NET, které jsou dostupné v jednotlivých implementace .NET.

Specifikaci .NET Standard se někdy označuje jako knihovna v dokumentaci. Protože knihovny zahrnuje implementace rozhraní API, nejen specifikace (rozhraní), je zavádějící pro volání .NET Standard "library". Chcete-li odstranit tohle využívání v dokumentaci ke službě, s výjimkou v souvislosti s aplikací název .NET Standard Microsoft.aspnetcore.all plánujeme (`NETStandard.Library`).

Zobrazit [.NET Standard](net-standard.md).

## <a name="ngen"></a>NGEN

Generování nativního (obrázek).

Tuto technologii si lze představit jako trvalé kompilátor JIT. Obvykle zkompiluje kód na počítači, kde je kód spuštěn, ale kompilace obvykle dochází v době instalace.

## <a name="package"></a>Balíček

Balíček NuGet &mdash; nebo právě balíčku &mdash; je *ZIP* soubor s minimálně jedno sestavení se stejným názvem, společně s další metadata, jako je například jméno autora.

*ZIP* soubor má *.nupkg* rozšíření a může obsahovat prostředky, jako například *.dll* soubory a *.xml* souborů pro použití s několika cílů architektury a verze. Při instalaci v aplikaci nebo knihovny, jsou vybrány příslušné prostředky založené na cílové rozhraní určené aplikace nebo knihovna. Prostředky, které definují rozhraní se nacházejí v *ref* složky a prostředky, které definují implementace *lib* složky.

## <a name="platform"></a>platforma

Operační systém a hardware, který běží na serveru, jako je například Windows, macOS, Linux, iOS a Android.

Tady jsou příklady použití v věty:

- ".NET core je na více platforem implementace rozhraní .NET." 
- "PCL profily představují platformy Microsoft, zatímco .NET Standard je nezávislé na platformě."

Dokumentace k .NET často používá "Platformu .NET" rozumí buď implementace .NET nebo zásobník .NET, včetně všech implementace. Obě tyto použití často zmatení s primární význam (operační systém a hardware), takže máme v plánu odstranění těchto použití v dokumentaci ke službě.

## <a name="runtime"></a>modul runtime

Prostředí pro spuštění spravované aplikace.

Operační systém je součástí prostředí modulu runtime, ale není součástí modulu runtime .NET. Tady je několik příkladů moduly runtime .NET:

- Common Language Runtime (CLR)
- Základní Common Language Runtime (CoreCLR)
- .NET native (pro UPW)
- Modul mono runtime

V dokumentaci k rozhraní .NET, někdy používá "runtime" jejich implementace .NET. Například v následujícím věty "runtime" by měla být nahrazena "implementace":

- "Různými moduly runtime .NET implementovat určité verze .NET Standard."
- "Knihovny, které jsou určeny ke spuštění ve více modulů – runtime by měl cíl tohoto rozhraní." (odkazující na .NET Standard)
- "Různými moduly runtime .NET implementovat určité verze .NET Standard. … Každá verze modulu runtime .NET inzeruje nejvyšší verze .NET Standard, kterou podporuje..."

Plánujeme, chcete-li odstranit tento nekonzistentní využití. 

## <a name="stack"></a>stack

Sada programování technologie, které se používají společně k vytváření a spouštění aplikací.

"Zásobník .NET" odkazuje na všechny implementace .NET a .NET Standard. Fráze "zásobník .NET" mohou odkazovat na jednu implementaci rozhraní .NET. 

## <a name="target-framework"></a>Cílová architektura

Kolekce rozhraní API, která aplikace .NET nebo knihovny se může spolehnout.

Aplikace nebo knihovny můžete cílení na verzi .NET Standard (například .NET Standard 2.0), což je specifikace pro standardizované sadu rozhraní API přes všechny implementace .NET. Aplikace nebo knihovna můžete také cílení na verzi konkrétní implementace rozhraní .NET, ve které malá a velká písmena získá přístup k rozhraním API specifický pro implementaci. Například aplikace, která se zaměřuje Xamarin.iOS získá přístup k rozhraní API pro zadaný Xamarin iOS obálky.

Pro některé cílové architektury (například rozhraní .NET Framework) k dispozici rozhraní API, které jsou definovány pomocí sestavení, která nainstaluje implementace .NET v systému, které mohou být aplikační rozhraní API (například ASP.NET, WinForms). Na základě balíčku cílových rozhraní (například .NET Standard a .NET Core) jsou rozhraní API určené balíčky, které jsou nainstalovány v aplikaci nebo knihovny. V takovém případě Cílová architektura, která určuje implicitně Microsoft.aspnetcore.all, který odkazuje na všechny balíčky, které společně tvoří rozhraní.

Zobrazit [platforem](frameworks.md).

## <a name="tfm"></a>TFM

Moniker cílového rozhraní framework.

Token standardizovaný formát pro zadání cílové rozhraní framework aplikace .NET nebo knihovny. Cílové architektury se obvykle odkazuje krátký název, jako například `net462`. Dlouhá Tfm (například. NETFramework, verze = 4.6.2) existuje, ale nejsou obecně používá k určení rozhraní .NET framework.

Zobrazit [platforem](frameworks.md).

## <a name="uwp"></a>UWP

Universal Windows Platform.

Implementace .NET, která je určená k vytváření moderních, dotykově ovládaný Windows aplikací a softwaru pro Internet věcí (IoT). Je určený ke sjednocení různé typy zařízení, které můžete chtít zaměřit, včetně počítače, tablety, phablets, telefony a dokonce i Xbox. UPW poskytuje mnoho služeb, jako jsou centralizované app storu, spouštěcí prostředí (AppContainer) a sada rozhraní API Windows nahrazujícím Win32 (WinRT). Aplikace může být napsané v jazyce C++, C#, VB.NET a JavaScript. Při použití jazyka C# a VB.NET, jsou k dispozici rozhraní API .NET pomocí .NET Core.

## <a name="see-also"></a>Viz také:

- [Průvodce technologií .NET](index.md)  
- [Průvodce rozhraním .NET Framework](../framework/index.md)  
- [.NET Core](../core/index.md)  
- [ASP.NET: Přehled](/aspnet/index#pivot=aspnet)  
- [Přehled ASP.NET Core](/aspnet/index#pivot=core)  
