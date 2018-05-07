---
title: Průvodce platformou .NET Core
description: .NET core je modulární a vysoce výkonné implementace rozhraní .NET pro vytváření aplikací pro Windows, Linuxu a Macu. Další informace o .NET Core začít pracovat.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: 7a2548a177f6e62e9c76c336c6e270a139d9fce0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-guide"></a>Průvodce platformou .NET Core

> Podívejte se [kurzy "Začínáme"](get-started.md) se dozvíte, jak vytvořit jednoduchou aplikaci .NET Core. Trvá jenom pár minut zprovoznění první aplikace.

.NET core je platforma pro vývoj univerzálních spravován společností Microsoft a komunitou .NET na [Githubu](https://github.com/dotnet/core). Je napříč platformami, podpora systému Windows, systému macOS a Linux a mohou být používány zařízení, cloud a scénáře vložených/IoT. 

Následující vlastnosti nejlepší definovat .NET Core:

- **Flexibilní nasazení:** lze zahrnout do vaší aplikace nebo nainstalovat vedle sebe uživatele – nebo celého systému.
- **Napříč platformami:** běží na systému Windows, systému macOS a Linux; může přenést do jiných operačních systémů. [Podporované operační systémy (OS)](https://github.com/dotnet/core/blob/master/roadmap.md), procesory a scénáře aplikací bude růst v čase, od společnosti Microsoft, další společnosti a jednotlivce.
- **Nástroje příkazového řádku:** všechny scénáře produktu můžete provést v příkazovém řádku. 
- **Kompatibilní:** .NET Core je kompatibilní s rozhraní .NET Framework, Xamarin a Mono, prostřednictvím [.NET Standard](../standard/net-standard.md).
- **S otevřeným zdrojem:** platformy .NET Core je open source, pomocí licencí MIT a Apache 2. Dokumentace je licencován [kopie podle](https://creativecommons.org/licenses/by/4.0/). Je .NET core [.NET Foundation](https://dotnetfoundation.org/) projektu.
- **Společnost Microsoft podporuje:** na společnost Microsoft, podporuje .NET Core [základní podpora v rozhraní .NET](https://www.microsoft.com/net/core/support/)

## <a name="composition"></a>Složení

.NET core se skládá z následujících částí:

- A [modulu runtime .NET](https://github.com/dotnet/coreclr), který poskytuje systém typů, načítání sestavení, systém uvolňování paměti, nativní interoperabilita a další základní služby. 
- Sadu [framework knihovny](https://github.com/dotnet/corefx), které poskytují základní nástroje primitivní datové typy, typy složení aplikace a. 
- A [sadu SDK nástroje](https://github.com/dotnet/cli) a [kompilátory jazyka](https://github.com/dotnet/roslyn) které umožňují prostředí základní vývojáře k dispozici v [.NET Core SDK](sdk.md).
- Hostitele aplikace 'dotnet', který se používá ke spouštění aplikací .NET Core. Vybere modul runtime a hostitelem modulu runtime, poskytuje načítání zásad sestavení a spuštění aplikace. Na stejném hostiteli je také použitý ke spuštění nástroje SDK mnohem stejným způsobem.

### <a name="languages"></a>Jazyky

Jazyky C#, Visual Basic a F # umožňuje psát aplikace a knihovny pro .NET Core. Kompilátory spustit na .NET Core umožňuje vyvíjet pro .NET Core kdekoli spustí. Obecně platí nebudete používat kompilátory přímo, ale nepřímo pomocí nástrojů sady SDK.

Kompilátory jazyka C#, Visual Basic a F # a nástrojů .NET Core jsou, nebo lze integrovat do několika textové editory a integrovaného vývojového prostředí, včetně Visual Studio, [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp), Sublime Text a Vim, provedení .NET Core vývoj možnost ve vaší Oblíbené položky kódování prostředí a operačního systému. Tato integrace poskytuje, v části dobrý zaměstnance z [OmniSharp projektu](http://www.omnisharp.net/).

### <a name="net-apis-and-compatibility"></a>Rozhraní API technologie .NET a kompatibility

.NET core můžete představit jako napříč platformami verze rozhraní .NET Framework, ve vrstvě z rozhraní .NET Framework základní třídy knihovny (BCL). Implementuje [.NET Standard](../standard/net-standard.md) specifikace. .NET core poskytuje podmnožinu rozhraní API, které jsou k dispozici v rozhraní .NET Framework nebo Mono nebo Xamarin. V některých případech typy nejsou implementované plně (některé členy nejsou k dispozici nebo byly přesunuty).

Podívejte se na [.NET Core plán](https://github.com/dotnet/core/blob/master/roadmap.md) Další informace o rozhraní API .NET Core plán.

### <a name="relationship-to-net-standard"></a>Vztah k rozhraní .NET Standard

[.NET Standard](../standard/net-standard.md) je specifikace rozhraní API, která popisuje konzistentní sadu rozhraní API .NET, která vývojářům můžete očekávat, že v každém implementace rozhraní .NET. Implementace rozhraní .NET je třeba implementovat tato specifikace, aby se považovala za standardem .NET Standard a k podpoře knihovny .NET standardní cílených. 

.NET core implementuje .NET Standard a proto podporuje .NET Standard knihovny.

### <a name="workloads"></a>Úkoly

.NET Core samostatně, obsahuje model jedné aplikace – aplikace konzoly –, což je užitečné pro nástroje, místní služby a hry založený na textu. Modely další aplikací mít byla nástavbou .NET Core rozšířit jeho funkce, jako například:

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 univerzální platformu Windows (UWP)](https://developer.microsoft.com/windows)
- [Pokud je cílem UWP Xamarin.Forms](https://www.xamarin.com/forms)

### <a name="open-source"></a>Open Source

[.NET core](https://github.com/dotnet/core) je open source (licencí MIT) a byla na podílí [.NET Foundation](https://dotnetfoundation.org) společností Microsoft v 2014. Teď je jeden z Nejaktivnější projektů Foundation rozhraní .NET. Ho můžete volně používat jednotlivce a společností, včetně pro osobní academic nebo obchodní účely. Více společností používá jako součást aplikace, nástroje, nové platformy a hostování služeb .NET Core. Některé z těchto společností udělat významné příspěvky .NET Core na Githubu a poskytovat pokyny k produktu směr jako součást [.NET Foundation technické řízení skupiny](https://dotnetfoundation.org/blog/tsg-welcome).

## <a name="acquisition"></a>Získání

.NET core se distribuuje dvěma hlavními způsoby, jako balíčky v NuGet.org a jako samostatné distribuce.

### <a name="distributions"></a>Distribuce

Je možné stáhnout .NET Core na [.NET Core Začínáme](https://www.microsoft.com/net/core) stránky.

- *Microsoft .NET Core* distribuční zahrnuje modul runtime CoreCLR, přidružené knihovny, hostitel aplikace konzoly a `dotnet` Spouštěč aplikace. Je popsán [ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) metapackage.
- *Microsoft .NET Core SDK* distribuční zahrnuje .NET Core a sadu nástrojů pro obnovování balíčků NuGet a kompilaci a sestavování aplikací. 

Obvykle nejprve nainstalujete .NET Core SDK začít s vývojem pro .NET Core. Můžete nainstalovat další sestavení .NET Core (možná předběžná).

### <a name="packages"></a>Balíčky

- [.NET core balíčky](packages.md) obsahovat .NET Core runtime a knihovny (referenční sestavení a implementace). Například [System.Net.Http](https://www.nuget.org/packages/System.Net.Http/).
- [.NET core Metapackages](packages.md) popisují různé vrstvy a aplikaci modely odkazem příslušné sady balíčky verzí knihovny.

## <a name="architecture"></a>Architektura

.NET core je implementace rozhraní .NET a platformy. Primární architektury obavy jedinečné pro .NET Core se vztahují k poskytnutí implementace specifické pro platformu pro podporované platformy.

### <a name="environments"></a>Prostředí

.NET core je podporován společností Microsoft v systému Windows, systému macOS a Linux. V systému Linux společnost Microsoft podporuje především .NET Core systémem Red Hat Enterprise Linux (RHEL) a Debian distribučních skupin.

.NET core aktuálně podporuje X64 procesory. V systému Windows je také podporována X86. ARM64 a ARM32 jsou v průběhu.

[.NET Core plán](https://github.com/dotnet/core/blob/master/roadmap.md) poskytuje podrobnější informace o zatížení a podpora prostředí operačního systému a využití procesoru a plány.

Další společnosti nebo skupiny můžou podporovat .NET Core pro jiné typy aplikací a prostředí.

### <a name="designed-for-adaptability"></a>Určená pro přizpůsobivost

.NET core byla vytvořena jako produkt velmi podobně jako u ale jedinečný relativně k ostatním produktům .NET. Má byly navržené tak, aby široký přizpůsobivost pro nové platformy pro nové úlohy a s novou toolchains kompilátoru. Má několik operačního systému a procesoru porty v průběhu a může být přesně do mnoho dalších. Příkladem je [LLILC](https://github.com/dotnet/llilc) projektu, který je časná prototyp nativní kompilace .NET Core prostřednictvím [LLVM](http://llvm.org/) kompilátoru.

Produkt je rozděleno do několika částí, povolení různých částí se přizpůsobí nové platformy na různé plány. Modul runtime a základní knihovny specifických pro platformy musí přenést jako jednotku. Bez ohledu na platformu knihovny by měly fungovat jako-je na všech platformách ve vytváření. Je projekt odchylka ke snížení specifické pro platformu implementace zvýšení efektivity developer, upřednostňují platformy jazykově neutrální kód C#, vždy, když algoritmus nebo rozhraní API může být implementováno v úplné nebo část tímto způsobem.

Osoby běžně požádat o tom, jak .NET Core implementují kvůli podpoře více operačních systémů. Obvykle vyzvou Pokud existují samostatné implementace nebo pokud [Podmíněná kompilace](https://en.wikipedia.org/wiki/Conditional_compilation) se používá. Je i s silné odchylka směrem Podmíněná kompilace.

Zobrazí se v grafu nižší, než je většina [CoreFX](https://github.com/dotnet/corefx) je platforma jazykově neutrální kód, který je sdílen na všech platformách. Kód platformy jazykově neutrální se dá implementovat jako jednoho přenosné sestavení, který se používá na všech platformách.

![CoreFX: Řádky kódu na každou platformu](../images/corefx-platforms-loc.png)

Implementace systému Windows a Unix jsou podobné velikost. Systém Windows má větší implementaci vzhledem k tomu, že CoreFX implementuje některé funkce pouze pro systém Windows, jako například [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) , ale ještě neimplementuje žádné jen Unix koncepty. Zobrazí se také, že většina implementace Linux a systému macOS jsou sdíleny ve implementace systému Unix, Linux a systému macOS konkrétní implementace jsou podobné zhruba velikost.


Existuje řada specifické pro platformu a nezávislé na platformě knihovny v .NET Core. Zobrazí se vzoru v několik příkladů:

- [CoreCLR](https://github.com/dotnet/coreclr) se liší podle platformy. Ho je součástí C/C++, takže se liší podle platformy ve vytváření.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) a [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) jsou specifické pro platformu, vzhledem k tomu, že kryptografie rozhraní API a úložiště, který výrazně liší na každý operační systém. 
- [System.Collections –](https://github.com/dotnet/corefx/tree/master/src/System.Collections) a [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) jsou platformy jazykově neutrální oznámeno, že jejich vytvoření a pracovat s datové struktury.

## <a name="comparisons-to-other-net-implementations"></a>Porovnání do jiné implementace rozhraní .NET

Pravděpodobně je to nejjednodušší provádět zjistit velikost a tvar .NET Core srovnáním stávající implementace rozhraní .NET. 

### <a name="comparison-with-net-framework"></a>Porovnání s rozhraním .NET Framework

Rozhraní .NET byla poprvé oznámeno společností Microsoft v 2000 a pak vyvinuly odtud. Rozhraní .NET Framework byl primární implementace rozhraní .NET vyprodukované Microsoft během tohoto rozpětí 15 + roku. 

Hlavní rozdíly mezi .NET Core a rozhraní .NET Framework: 

- **Modely aplikace** – .NET Core nepodporuje všechny rozhraní .NET Framework aplikace – modely, v části protože řada z nich jsou postavené na systému Windows technologií, jako je například grafického subsystému WPF (nástavbou DirectX). Konzola a ASP.NET Core aplikace modely jsou podporovány .NET Core a rozhraní .NET Framework. 
- **Rozhraní API** – .NET Core obsahuje mnoho stejných, ale méně, rozhraní API jako rozhraní .NET Framework a pomocí různých řešení (názvy sestavení se liší; obrazce typu se liší v klíče případech). Tyto rozdíly aktuálně obvykle vyžadují změny k portu zdroji .NET Core. .NET core implementuje [.NET Standard](../standard/net-standard.md) rozhraní API, které se zvýší zahrnout další rozhraní API BCL rozhraní .NET Framework v čase.
- **Subsystémy** – .NET Core implementuje podmnožinu subsystémy v rozhraní .NET Framework, s cílem jednodušší implementaci a programovací model. Například není podporována zabezpečení přístupu kódu (CAS), když je podporované reflexe.
- **Platformy** – rozhraní .NET Framework podporuje Windows a Windows Server, ale také podporuje .NET Core systému macOS a Linux.
- **Otevřít zdroj** – .NET Core je open source, zatímco [jen pro čtení podmnožinu rozhraní .NET Framework](https://github.com/microsoft/referencesource) je open source.

Když .NET Core jedinečný a má významné rozdíly pro rozhraní .NET Framework a jiné implementace rozhraní .NET, je jednoduchá sdílet kódu, pomocí buď zdroj nebo binární sdílení techniky. 

### <a name="comparison-with-mono"></a>Porovnání s Mono

[Mono](http://www.mono-project.com/) je původní platformy a [s otevřeným zdrojem](https://github.com/mono/mono) implementace rozhraní .NET, nejprve přesouvání v 2004. Ho můžete představit jako klon komunity rozhraní .NET Framework. Monofonní projektový tým spoléhali na open [.NET standardy](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (zejména 335 ECMA) aby bylo zajištění kompatibilní implementace publikovat společností Microsoft.

Hlavní rozdíly mezi .NET Core a Mono:

- **Modely aplikace** – Mono podporuje podmnožinu aplikace rozhraní .NET Framework – modely (například Windows Forms) a některé další ty (například [Xamarin.iOS](https://www.xamarin.com/platform)) prostřednictvím produktu Xamarin. .NET core nepodporuje tyto.
- **Rozhraní API** – podporuje Mono [velká část](http://docs.go-mono.com/?link=root%3a%2fclasslib) rozhraní .NET Framework rozhraní API, použijte stejné názvy sestavení a řešení.
- **Platformy** – Mono podporuje mnoho platformy a procesory.
- **Otevřít zdroj** – Mono a .NET Core jak používat licencí MIT a jsou projekty .NET Foundation.
- **Fokus** – hlavním cílem tohoto Mono v posledních letech je mobilní platformy, zatímco .NET Core se zaměřuje na cloudu úlohy.
