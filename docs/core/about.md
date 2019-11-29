---
title: O platformě .NET Core
description: Přečtěte si o .NET Core.
ms.date: 09/17/2019
ms.openlocfilehash: 4fe16475e18eb88e88fb33d30508f9ef5c9f2cd5
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552245"
---
# <a name="about-net-core"></a>O platformě .NET Core

.NET Core má následující vlastnosti:

- **Pro různé platformy:** Spouští se v [operačních systémech](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, MacOS a Linux.
- **Konzistentní napříč architekturami:** Spustí váš kód se stejným chováním na více architekturách, včetně x64, x86 a ARM.
- **Nástroje příkazového řádku:**  Zahrnuje snadno použitelné nástroje příkazového řádku, které se dají použít pro místní vývoj a scénáře nepřetržité integrace.
- **Flexibilní nasazení:** Může být součástí vaší aplikace nebo nainstalovaná souběžně (instalace na úrovni uživatele nebo systému). Dá se použít s [kontejnery Docker](docker/introduction.md).
- **Kompatibilní:** .NET Core je kompatibilní s .NET Framework, Xamarin a Mono prostřednictvím [.NET Standard](../standard/net-standard.md).
- **Open Source:** Platforma .NET Core je open source pomocí licencí MIT a Apache 2. .NET Core je projekt [.NET Foundation](https://dotnetfoundation.org/) .
- **Podporováno Microsoftem:** podpora .NET Core je podporovaná Microsoftem na [podporu .NET Core](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Jazyky

C#, Visual Basic a F# jazyky lze použít k psaní aplikací a knihoven pro .NET Core. Tyto jazyky lze použít ve vašem oblíbeném textovém editoru nebo integrovaném vývojovém prostředí (IDE), včetně:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
- Text podvápna
- Vim

Tato integrace je součástí, a to přispěvateli projektů [OmniSharp](https://www.omnisharp.net/) a [Ionide](http://ionide.io) .

## <a name="apis"></a>API

Rozhraní .NET Core zpřístupňuje rozhraní API pro mnoho scénářů, z nichž několik sleduje:

- Primitivní typy, například <xref:System.Boolean?displayProperty=nameWithType> a <xref:System.Int32?displayProperty=nameWithType>.
- Kolekce, například <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Typy nástrojů, například <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>a <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Datové typy, například <xref:System.Data.DataSet?displayProperty=nameWithType>a [negenerickými](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Vysoce výkonné typy, například <xref:System.Numerics.Vector?displayProperty=nameWithType> a [kanály](https://devblogs.microsoft.com/dotnet/system-io-pipelines-high-performance-io-in-net/).

.NET Core poskytuje kompatibilitu s rozhraními API .NET Framework a mono implementací specifikace [.NET Standard](../standard/net-standard.md) .

## <a name="frameworks"></a>Architektury

Na rozhraní .NET Core bylo postaveno více platforem:

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 Univerzální platforma Windows (UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Složení

.NET Core se skládá z následujících částí:

- [Modul runtime .NET Core](https://github.com/dotnet/coreclr), který poskytuje systém typů, načítání sestavení, systém uvolňování paměti, nativní spolupráci a další základní služby. [Knihovny .NET Core Framework](https://github.com/dotnet/corefx) poskytují primitivní datové typy, typy kompozic aplikací a základní nástroje.
- [Běhový modul ASP.NET](https://github.com/aspnet/home), který poskytuje rozhraní pro vytváření moderních cloudových aplikací připojených k Internetu, jako jsou webové aplikace, aplikace IoT a mobilní back-endy.
- [Nástroje .NET Core CLI](https://github.com/dotnet/cli) a jazykové kompilátory ([Roslyn](https://github.com/dotnet/roslyn) a [F#](https://github.com/microsoft/visualfsharp)), které umožňují prostředí pro vývojáře .NET Core.
- [Nástroj dotnet](https://github.com/dotnet/core-setup), který se používá ke spouštění aplikací .NET Core a nástrojů rozhraní příkazového řádku. Vybírá modul runtime a hostuje modul runtime, poskytuje zásady načítání sestavení a spouští aplikace a nástroje.

Tyto součásti jsou distribuovány následujícími způsoby:

- [.NET Core Runtime](https://dotnet.microsoft.com/download) – zahrnuje knihovny runtime .NET Core a architektury rozhraní.
- [ASP.NET Core Runtime](https://dotnet.microsoft.com/download) --zahrnuje ASP.NET Core a modul runtime .NET Core a knihovny rozhraní.
- [.NET Core SDK](https://dotnet.microsoft.com/download) – zahrnuje nástroje rozhraní .NET CLI, ASP.NET Core Runtime a .NET Core Runtime a rozhraní.

### <a name="open-source"></a>Open source

[.NET Core](https://github.com/dotnet/core) je open source ([licence MIT](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) a přispělo se k [.net Foundation](https://dotnetfoundation.org) od Microsoftu v 2014. Teď je to jeden z nejaktivnějších projektů .NET Foundation. Může je používat jednotlivci a společnosti, včetně pro osobní, školní nebo komerční účely. Několik společností používá .NET Core jako součást aplikací, nástrojů, nových platforem a hostitelských služeb. Některé z těchto společností mají významné příspěvky na rozhraní .NET Core na GitHubu a poskytují pokyny pro směr produktu v rámci [skupiny technického řízení .NET Foundation](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Navrženo pro zajištění přizpůsobivosti

.NET Core se v porovnání s jinými produkty .NET sestavil jako velmi podobný, ale jedinečný produkt. Byla navržena tak, aby umožňovala širokou škálu nových platforem a úloh a má k dispozici několik operačních systémů a portů procesoru (a je možné ji přenést na mnoho dalších).

Produkt je rozdělen do několika částí a umožňuje v různých časech přizpůsobení různých částí novým platformám. Základní knihovny pro modul runtime a specifické pro platformu musí být přeportované jako jednotka. Nezávislá knihovny platforem by měly fungovat tak, jak jsou na všech platformách, podle konstrukce. Existuje posun projektu pro snížení implementace specifických pro konkrétní platformu, aby se zvýšila efektivita vývojářů, přičemž se C# kód neutrální pro platformu musí považovat za plný nebo nějakým způsobem implementovat rozhraní API.

Lidé často žádají, jak je .NET Core implementováno, aby podporovalo více operačních systémů. Obvykle se dotazují, jestli existují samostatné implementace nebo když se používá [Podmíněná kompilace](https://en.wikipedia.org/wiki/Conditional_compilation) . Je to obojí se silným posunem směrem k podmíněné kompilaci.

V následujícím grafu vidíte, že velká většina [CoreFX](https://github.com/dotnet/corefx) je neutrální kód platformy, který je sdílen napříč všemi platformami. Kód neutrální pro platformu je možné implementovat jako jedno přenosné sestavení, které se používá na všech platformách.

![CoreFX: řádky kódu na platformu](../images/corefx-platforms-loc.png)

Implementace Windows a UNIX mají stejnou velikost. Systém Windows má větší implementaci, protože CoreFX implementuje některé funkce pouze pro systém Windows, například [Microsoft. Win32. Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) , ale ještě neimplementuje mnoho konceptů pouze pro systém UNIX. Uvidíte také, že většina implementací systémů Linux a macOS je sdílena v rámci implementace systému UNIX, zatímco implementace týkající se systémů Linux a macOS mají přibližně stejnou velikost.

Rozhraní .NET Core obsahuje kombinaci knihoven specifických pro platformu a platforem neutrálních na platformě. Vzor si můžete prohlédnout v několika příkladech:

- [CoreCLR](https://github.com/dotnet/coreclr) je specifický pro platformu. Sestavuje se nad subsystémy operačního systému, jako je správce paměti a Plánovač vláken.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) a [System. Security. Cryptography.](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) Algorithms jsou specifické pro platformu, protože rozhraní API pro úložiště a kryptografii se v každém operačním systému liší.
- [System. Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) a [System. Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) jsou neutrální vzhledem k tomu, že vytvářejí a pracují nad datovými strukturami.

## <a name="comparisons-to-other-net-implementations"></a>Porovnání s jinými implementacemi .NET

Je pravděpodobně snazší pochopit velikost a tvar rozhraní .NET Core porovnáním s existujícími implementacemi .NET.

### <a name="comparison-with-net-framework"></a>Porovnání s .NET Framework

Rozhraní .NET bylo poprvé oznámeno společností Microsoft v 2000 a pak se z něj vyvinulo. .NET Framework byla primární implementace .NET, kterou vytvořila společnost Microsoft, během této doby skoro dvě desetiletí.

Hlavní rozdíly mezi .NET Core a .NET Framework:

- **Modely aplikací** --. .NET Core nepodporují všechny modely .NET Framework aplikací. Konkrétně nepodporuje webové formuláře ASP.NET a ASP.NET MVC, ale podporuje ASP.NET Core MVC. A Počínaje rozhraním .NET Core 3,0 podporuje .NET Core také WPF a model Windows Forms pouze v systému Windows.
- **Rozhraní api** --. NET Core obsahuje velkou podmnožinu .NET Framework základní knihovny tříd s jiným přífaktoringem (názvy sestavení se liší. Členové vystaveni u typů se liší v klíčových případech). V některých případech tyto rozdíly vyžadují změny ve zdroji portů rozhraní .NET Core. Další informace najdete v tématu [analyzátor přenositelnosti .NET](../standard/analyzers/portability-analyzer.md). .NET Core implementuje specifikaci rozhraní [.NET Standard](../standard/net-standard.md) API.
- **Subsystémy** --. NET Core implementují podmnožinu subsystémů v .NET Framework s cílem jednoduššího implementačního a programovacího modelu. Například zabezpečení přístupu kódu (CAS) není podporováno, zatímco je reflexe podporována.
- **Platformy** – .NET Framework podporuje Windows a Windows Server, zatímco .NET Core podporuje taky MacOS a Linux.
- **Open source** --. NET Core je open source, zatímco [podmnožina .NET Framework jen pro čtení](https://github.com/microsoft/referencesource) je open source.

I když je .NET Core jedinečné a má významné rozdíly v .NET Framework a dalších implementacích .NET, je jednoduché sdílet kód mezi těmito implementacemi pomocí metod zdrojového nebo binárního sdílení.

Vzhledem k tomu, že .NET Core podporuje souběžnou instalaci a její modul runtime je zcela nezávislý na .NET Framework, lze ji nainstalovat na počítače s .NET Framework nainstalovány bez problémů.

### <a name="comparison-with-mono"></a>Porovnání s mono

[Mono](https://www.mono-project.com/) je původní implementace .NET pro více platforem. Začala jako [Open-Source](https://github.com/mono/mono) alternativa pro .NET Framework a přechodem do cílení na mobilní zařízení jako zařízení s iOS a Androidem se stala oblíbená. Dá se představit za klonování komunity .NET Framework. Projektový tým mono se spoléhal na otevřené [standardy .NET](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (zejména ECMA 335) publikované společností Microsoft za účelem poskytování kompatibilní implementace.

Hlavní rozdíly mezi .NET Core a mono:

- **Modely aplikací** – mono podporuje podmnožinu .NET Frameworkch modelů aplikací (například model Windows Forms) a několik dalších pro vývoj pro mobilní zařízení (například [Xamarin. iOS](https://www.xamarin.com/platform)) prostřednictvím produktu Xamarin. .NET Core nepodporuje Xamarin.
- **Rozhraní API** – mono podporuje [velkou podmnožinu](http://docs.go-mono.com/?link=root%3a%2fclasslib) rozhraní .NET Framework API, s použitím stejných názvů sestavení a faktoringu.
- **Platformy** – mono podporuje spoustu platforem a procesorů.
- **Open Source** – mono a .NET Core používají jak licenci technologie MIT, tak projekty .NET Foundation.
- **Zaměření** – hlavním cílem mono v posledních letech jsou mobilní platformy, zatímco .NET Core se zaměřuje na úlohy cloudu a stolních počítačů.

## <a name="the-future"></a>Budoucnost

Bylo oznámeno, že .NET 5 bude novou verzí .NET Core a představuje sjednocení platformy. Projekt se zaměřuje na vylepšení .NET v několika klíčových způsobech:

- Vytvořte jeden modul runtime .NET a rozhraní, které lze použít všude a který má jednotné běhové chování a vývojářské prostředí.
- Rozšiřte možnosti .NET tak, že vyberete nejlepší z rozhraní .NET Core, .NET Framework, Xamarin a mono.
- Sestavujte tento produkt z jednoho základu kódu, který můžou vývojáři (Microsoft a komunita) pracovat společně a rozšiřovat všechny scénáře.

Další podrobnosti o tom, co se plánuje pro .NET 5, najdete v tématu [představení rozhraní .NET 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/).
