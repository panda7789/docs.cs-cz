---
title: Informace o .NET Core
description: Další informace o .NET Core.
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.openlocfilehash: d9943246b683c8fd892e7bc5fd09a10b72e31a5f
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326391"
---
# <a name="about-net-core"></a>Informace o .NET Core

.NET core má následující vlastnosti:

- **Různé platformy:** běží na Windows, macOS a Linux [operačních systémů](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md).
- **Konzistentní vzhledem k aplikacím v architekturách:** spustí váš kód s stejné chování na několik architektur, včetně x64 x86 a ARM.
- **Nástroje příkazového řádku:** obsahuje – pomocí nástroje příkazového řádku, která se používá pro místní vývoj a ve scénářích průběžnou integraci.
- **Flexibilní nasazení:** mohou být součástí vaší aplikace nebo nainstalovat vedle sebe uživatele – nebo celý počítač. Je možné s [kontejnery Dockeru](docker/index.md).
- **Kompatibilní:** .NET Core je kompatibilní s rozhraní .NET Framework, Xamarin a Mono, prostřednictvím [.NET Standard](../standard/net-standard.md).
- **Otevřít zdroj:** platformy .NET Core je open source, použitím licencí MIT a Apache 2. .NET core je [.NET Foundation](https://dotnetfoundation.org/) projektu.
- **Společnost Microsoft podporuje:** na společnost Microsoft, podporuje .NET Core [podpora platformy .NET Core](https://www.microsoft.com/net/core/support/).

## <a name="languages"></a>Jazyky

Jazyky C#, Visual Basic a F # umožňuje psát aplikace a knihovny pro .NET Core. Tyto jazyky jsou, nebo je možné integrovat do oblíbených textových editorů a prostředí IDE, včetně [sady Visual Studio](https://visualstudio.microsoft.com/vs/), [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp), Sublime Text a Vim. Tato integrace poskytuje, částečně dobrý lidé z [OmniSharp](http://www.omnisharp.net/) a [Ionide](http://ionide.io) projekty.

## <a name="apis"></a>API

.NET core zveřejňuje rozhraní API pro většinu scénářů, postupujte podle několik z nich:

- Primitivní typy, jako například [bool] [ bool] a [int][int].
- Kolekce, jako například <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Nástroj pro typy, jako například <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>, a <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Datové typy, jako například <xref:System.Data.DataSet?displayProperty=nameWithType>, a [DbSet][dbset].
- Vysoký výkon typy, jako například <xref:System.Numerics.Vector?displayProperty=nameWithType> a [kanály][pipelines].

.NET core zajišťuje kompatibilitu se rozhraní .NET Framework a rozhraní API Mono implementací [.NET Standard](../standard/net-standard.md) specifikace.

[bool]: https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/bool
[int]: https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/int
[pipelines]: https://blogs.msdn.microsoft.com/dotnet/2018/07/09/system-io-pipelines-high-performance-io-in-net/
[dbset]: https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/

## <a name="frameworks"></a>Rozhraní

Nad rámec .NET Core jsou sestavené několik architektur:

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 Universal Windows Platform (UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Složení

.NET core se skládá z následujících částí:

- [.NET Core runtime](https://github.com/dotnet/coreclr), která poskytuje systém typů, načítání sestavení, systému uvolňování paměti, nativní zprostředkovatel komunikace s objekty a dalších základních služeb. [Knihovny .NET core framework](https://github.com/dotnet/corefx) poskytují základní nástroje, typy složení aplikace a primitivní datové typy.
- [Modul runtime ASP.NET](https://github.com/aspnet/home), který poskytuje architekturu pro vytváření moderních cloudových založené na Internetu připojené aplikace, například webové aplikace, aplikace IoT a mobilních back-endů.
- [Nástroje rozhraní příkazového řádku .NET Core](https://github.com/dotnet/cli) a kompilátory jazyka ([Roslyn](https://github.com/dotnet/roslyn) a [F #](https://github.com/microsoft/visualfsharp)) umožňující prostředí pro vývojáře .NET Core.
- [Nástrojů dotnet](https://github.com/dotnet/core-setup), který se používá ke spuštění aplikace .NET Core a nástroje příkazového řádku. Vybere modul runtime a hostitelem modulu runtime, poskytuje načítání zásady sestavení a spuštění aplikace a nástroje.

Tyto součásti jsou distribuovány následujícími způsoby:

- [.NET core Runtime](https://www.microsoft.com/net/download/dotnet-core/2.1) – zahrnuje knihovny modulu runtime a rozhraní .NET Core.
- [ASP.NET Core Runtime](https://www.microsoft.com/net/download/dotnet-core/2.1) – obsahuje knihovny modulu runtime a rozhraní framework ASP.NET Core a .NET Core.
- [Sada .NET core SDK](https://www.microsoft.com/net/download/dotnet-core/2.1) – zahrnuje nástroje rozhraní příkazového řádku .NET, ASP.NET Core runtime a modulu runtime .NET Core a rozhraní framework.

### <a name="open-source"></a>Open Source

[.NET core](https://github.com/dotnet/core) je open source ([licencí MIT](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) a bylo přispět k [.NET Foundation](https://dotnetfoundation.org) od Microsoftu v roce 2014. Nyní je jeden z projektů .NET Foundation Nejaktivnější. Ho můžete volně přijímá jednotlivce a společností, včetně osobních, akademický nebo obchodní účely. Více společností používá jako součást aplikace, nástroje, nové platformy a hostování služeb .NET Core. Některé z těchto společnostech výrazně přispějeme k .NET Core na Githubu a poskytnout Rady ohledně směr produktu jako součást [.NET Foundation technické řízení skupiny](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Navržené pro přizpůsobivost

.NET core je sestavený Build jako produkt velmi podobné, ale jedinečné vzhledem k produkty .NET. Byla navržena tak, aby povolit široké přizpůsobivost na nové platformy a úlohy. Má několik operačního systému a procesor portů jsou k dispozici a může přenést do mnoha dalších.

Produkt je rozdělená do několika částí, povolení různých částí se přizpůsobí nové platformy v různých časech. Modul runtime a základní knihovny pro konkrétní platformu musíte přenést jako celek. Nezávislý na platformě knihovny by měly fungovat jako-je na všech platformách pomocí vytváření. Je posun projektu ke snížení implementace specifické pro platformu na zvýšení efektivity pro vývojáře, preferují platformy neutrální kód jazyka C# pokaždé, když se algoritmus nebo rozhraní API je možné implementovat v celé nebo části tímto způsobem.

Uživatelé často ptají, jak .NET Core je implementovaná za účelem podpory více operačních systémů. Obvykle žádá Pokud existují samostatné implementace nebo [podmíněné kompilace](https://en.wikipedia.org/wiki/Conditional_compilation) se používá. Je i s silné Posun směrem k podmíněné kompilace.

Zobrazí se v grafu pod ním drtivou většinu [CoreFX](https://github.com/dotnet/corefx) je platforma doménově neutrální kód, který se sdílí mezi všemi platformami. Platforma doménově neutrální kód je možné implementovat jako jediné přenosných sestavení, který se používá na všech platformách.

![CoreFX: Řádky kódu pro každou platformu](../images/corefx-platforms-loc.png)

Implementace Windows a Unix se podobají velikost. Windows má větší implementaci, protože CoreFX implementuje některé funkce jen pro Windows, jako například [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) ale ještě neimplementuje mnohé koncepty jen pro systém Unix. Uvidíte také, že většina operačních systémů Linux a macOS implementace jsou sdíleny napříč implementace systému Unix, Linux a macOS konkrétní implementace jsou zhruba podobní velikosti.

Existují kombinaci specifických pro platformu a platformy neutrální knihoven v .NET Core. Zobrazí se model v pár příkladů:

- [CoreCLR](https://github.com/dotnet/coreclr) se liší podle platformy. Postavená subsystémy operačního systému, stejně jako správce paměti a podproces plánovač.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) a [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) jsou specifické pro platformu, že úložiště a šifrování rozhraní API se liší na každý operační systém.
- [System.Collections –](https://github.com/dotnet/corefx/tree/master/src/System.Collections) a [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) jsou nezávislá na platformě, že uživatelé vytvářet a provozovat prostřednictvím datové struktury.

## <a name="comparisons-to-other-net-implementations"></a>Porovnávání v jiných implementacích rozhraní .NET

Je pravděpodobně nejjednodušším pochopit velikosti a tvaru .NET Core srovnáním stávající implementace .NET.

### <a name="comparison-with-net-framework"></a>Porovnání s rozhraním .NET Framework

.NET bylo poprvé oznámena společností Microsoft v 2000 a pak se z něj. Rozhraní .NET Framework byl primární vyrobená společností Microsoft, které v daném období téměř dva desetiletí implementace .NET.

Hlavní rozdíly mezi .NET Core a .NET Framework:

- **Modely aplikace** – .NET Core nepodporuje všechny rozhraní .NET Framework aplikace – modely. Konkrétně se nepodporuje, webových formulářů ASP.NET a MVC. Jsme představili, který [bude podporovat .NET Core 3, WPF a Windows Forms](https://blogs.msdn.microsoft.com/dotnet/2018/05/07/net-core-3-and-support-for-windows-desktop-applications/).
- **Rozhraní API** – .NET Core obsahuje velká podmnožina knihovna tříd rozhraní .NET Framework základ, s jinou řešení (se liší názvy sestavení; členy zveřejněné na typy se liší v klíčových případů). Tyto rozdíly vyžadovat změny do zdroje port až po .NET Core v některých případech (viz [microsoft/dotnet-apiport](https://github.com/microsoft/dotnet-apiport)). Implementuje .NET core [.NET Standard](../standard/net-standard.md) specifikace rozhraní API.
- **Subsystémy** – .NET Core v rozhraní .NET Framework, s cílem programovací model a jednodušší implementace implementuje podmnožinu subsystémů. Například není podporována zabezpečení přístupu kódu (CAS), i když se podporuje reflexe.
- **Platformy** – rozhraní .NET Framework podporuje Windows a Windows Server a .NET Core podporuje také macOS a Linux.
- **Open Source** – .NET Core je open source, zatímco [jen pro čtení podmnožinou rozhraní .NET Framework](https://github.com/microsoft/referencesource) je open source.

.NET Core je jedinečný a má významné rozdíly pro rozhraní .NET Framework a jiné implementace .NET, je jednoduché sdílení kódu mezi tyto implementace pomocí zdroje nebo binární sdílení techniky.

### <a name="comparison-with-mono"></a>Porovnání s Mono

[Mono](http://www.mono-project.com/) je původní napříč platformami a [opensourcových](https://github.com/mono/mono) implementace .NET, nejprve dodání 2004. To můžete představit jako klon komunity rozhraní .NET Framework. Týmový projekt Mono spoléhal na otevřený [.NET standardy](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (zejména 335 Standard ECMA) vydávaný microsoftem, aby bylo možné poskytovat kompatibilní implementace.

Hlavní rozdíly mezi Mono a .NET Core:

- **Modely aplikace** --Mono podporuje podmnožinu aplikace rozhraní .NET Framework – modely (třeba Windows Forms) a některé další značky (například [Xamarin.iOS](https://www.xamarin.com/platform)) prostřednictvím produktu Xamarin. .NET core nepodporuje tyto.
- **Rozhraní API** --Mono podporuje [velká podmnožina](http://docs.go-mono.com/?link=root%3a%2fclasslib) rozhraní API .NET Framework, použijte stejné názvy sestavení a které budou zohledňovat.
- **Platformy** – Mono podporuje mnoho platforem a procesorů.
- **Open Source** – Mono a .NET Core jak používat licencí MIT a jsou projekty .NET Foundation.
- **Fokus** – hlavním cílem Mono v posledních letech je mobilní platformy .NET Core se zaměřuje na cloud a aplikaci desktop úlohy.
