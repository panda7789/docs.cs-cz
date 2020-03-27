---
title: Přehled .NET Core
description: Zjistěte o charakteristikách a složení jádra .NET a porovnejte je s jinými implementacemi rozhraní .NET.
ms.date: 09/17/2019
ms.openlocfilehash: f2f97fe6a5f822266582c443fd916c270cb0cb6a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345201"
---
# <a name="net-core-overview"></a>Přehled .NET Core

.NET Core má následující charakteristiky:

- **Multiplatformní:** Běží na [operačních systémech](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, macOS a Linux .
- **Konzistentní napříč architekturami:** Spustí váš kód se stejným chováním na více architekturách, včetně x64, x86 a ARM.
- **Nástroje příkazového řádku:**  Obsahuje snadno použitelné nástroje příkazového řádku, které lze použít pro místní vývoj a ve scénářích průběžné integrace.
- **Flexibilní nasazení:** Může být součástí aplikace nebo nainstalována vedle sebe (instalace v rámci celého uživatele nebo systému). Lze použít s [kontejnery Dockeru](docker/introduction.md).
- **Kompatibilní:** .NET Core je kompatibilní s implementacemi .NET Framework, Xamarin a Mono přes [.NET Standard](../standard/net-standard.md).
- **Open source:** Platforma .NET Core je open source, používá licence MIT a Apache 2. .NET Core je projekt [.NET Foundation.](https://dotnetfoundation.org/)
- **Podporováno společností Microsoft:** .NET Core je [podporováno společností Microsoft](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Jazyky

Jazyky C#, Visual Basic a F# lze použít k zápisu aplikací a knihoven pro .NET Core. Tyto jazyky lze použít ve vašem oblíbeném textovém editoru nebo integrovaném vývojovém prostředí (IDE), včetně:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Kód visual studia](https://code.visualstudio.com/download)
- Vznešený text
- Vim

Editor integrace je poskytována částečně přispěvateli [omnisharp](https://www.omnisharp.net/) a [ionide](http://ionide.io) projektů.

## <a name="apis"></a>Rozhraní API

Mnoho api jsou zahrnuty, které splňují běžné potřeby, jako jsou:

- Primitivní typy, <xref:System.Boolean?displayProperty=nameWithType> například a <xref:System.Int32?displayProperty=nameWithType>.
- Kolekce, například <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>a .
- Typy užitkových nástrojů, například <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>, a <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Datové typy, <xref:System.Data.DataSet?displayProperty=nameWithType>například , a [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Vysoce výkonné typy, <xref:System.Numerics.Vector?displayProperty=nameWithType> například [a Pipelines](../standard/io/pipelines.md).

Jádro .NET poskytuje kompatibilitu s rozhraními .NET Framework a Mono API implementací specifikace [.NET Standard.](../standard/net-standard.md)

## <a name="frameworks"></a>Rozhraní

Na rozhraní .NET Core bylo postaveno více architektur, včetně:

- [ASP.NET Core](/aspnet/core/)
- [Univerzální platforma Windows (UPW)](/windows/uwp/)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Složení

.NET Core se skládá z následujících částí:

- [Zaběhu .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), který poskytuje typ systému, načítání sestavení, uvolňování paměti, nativní interop a další základní služby. [Knihovny rozhraní .NET Core framework](https://github.com/dotnet/runtime/tree/master/src/libraries) poskytují primitivní datové typy, typy složení aplikací a základní nástroje.
- [ASP.NET Core runtime](https://github.com/dotnet/aspnetcore), který poskytuje rámec pro vytváření moderních cloudových aplikací připojených k internetu, jako jsou webové aplikace, aplikace IoT a mobilní back-endy.
- Sada [.NET Core SDK](https://github.com/dotnet/sdk) a kompilátory jazyka ([Roslyn](https://github.com/dotnet/roslyn) a [F#](https://github.com/microsoft/visualfsharp)), které umožňují vývojářské prostředí .NET Core.
- Příkaz dotnet , který se používá ke spuštění aplikací .NET Core a příkazů příkazu příkazu příkazu příkazu příkazu příkazu příkazu.The [dotnet command](./tools/dotnet.md), which is used to launch .NET Core apps and CLI commands. Vybere a hostuje za běhu, poskytuje zásady načítání sestavení a spouští aplikace a nástroje.

Tyto součásti jsou distribuovány následujícími způsoby:

- [.NET Core Runtime](https://dotnet.microsoft.com/download) -- zahrnuje .NET Core runtime a framework knihovny.
- [ASP.NET Core Runtime](https://dotnet.microsoft.com/download) – zahrnuje ASP.NET core a .NET Core runtime a framework knihovny.
- [Sada .NET Core SDK](https://dotnet.microsoft.com/download) – zahrnuje rozhraní CLI jádra .NET, ASP.NET core runtime a .NET Core runtime a framework.

### <a name="open-source"></a>Open source

[.NET Core](https://github.com/dotnet/core) je open source[(licence MIT](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) a v roce 2014 byl microsoftem přispěl do [.NET Foundation.](https://dotnetfoundation.org) Nyní je jedním z nejaktivnějších projektů .NET Foundation. Může být používán jednotlivci a společnostmi, včetně pro osobní, akademické nebo komerční účely. Více společností používá .NET Core jako součást aplikací, nástrojů, nových platforem a hostingových služeb. Některé z těchto společností významně přispívají k .NET Core na GitHubu a poskytují pokyny ke směru produktu v rámci [technické řídící skupiny .NET Foundation](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Navrženo pro přizpůsobivost

.NET Core byl vytvořen jako podobný, ale jedinečný produkt ve srovnání s jinými produkty .NET. Byl navržen tak, aby umožnil širokou přizpůsobivost novým platformám a úlohám a má k dispozici několik portů operačního systému a procesoru (a může být přenesen o mnoho dalších).

Výrobek je rozdělen na několik kusů, což umožňuje přizpůsobit různé části novým platformám v různých časech. Runtime a platformy specifické pro základní knihovny musí být portován jako celek. Knihovny agnostiky na platformě by měly fungovat tak, jak jsou na všech platformách, a to na základě výstavby. Existuje zkreslení projektu směrem ke snížení implementace specifické pro platformu ke zvýšení efektivity vývojářů, raději platformy neutrální Kód C# vždy, když algoritmus nebo rozhraní API může být implementována v plném rozsahu nebo částečně tímto způsobem.

Lidé se běžně ptají, jak je implementováno rozhraní .NET Core za účelem podpory více operačních systémů. Obvykle se ptají, pokud existují samostatné implementace nebo pokud se používá [podmíněná kompilace.](https://en.wikipedia.org/wiki/Conditional_compilation) Je to obojí, se silnou zaujatostí vůči podmíněné kompilaci.

V následujícím grafu je vidět, že drtivá většina [knihoven .NET Core](https://github.com/dotnet/runtime/tree/master/src/libraries) je kompilována z neutrálního kódu platformy, který je sdílen na všech platformách. Neutrální kód platformy lze implementovat jako jediné přenosné sestavení, které se používá na všech platformách.

![CoreFX: Řádky kódu na platformu](../images/corefx-platforms-loc.png)

Implementace Systému Windows a Unixu mají podobnou velikost. Implementace systému Windows obsahuje některé funkce pouze pro systém Windows, například [Microsoft.Win32.Registry](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry), ale ještě neimplementuje mnoho konceptů pouze unixu. Velká část linuxových a macOS implementací je sdílena v implementaci Unixu. Implementace specifické pro Linux a macOS jsou podobné velikosti.

V rozhraní .NET Core je kombinace knihoven specifických pro platformu a neutrálních na platformě. Vzor můžete vidět v několika příkladech:

- [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) je specifické pro platformu. Staví na horní části subsystémů operačního systému, jako správce paměti a plánovač vláken.
- [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) a [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) jsou specifické pro platformu, vzhledem k tomu, že úložiště a kryptografické api se liší v každém osu.
- [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) a [System.Linq](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) jsou neutrální z platformy vzhledem k tomu, že vytvářejí a pracují přes datové struktury.

## <a name="comparisons-to-other-net-implementations"></a>Porovnání s jinými implementacemi rozhraní .NET

Chcete-li porozumět velikosti a tvaru jádra .NET, porovnejte je v následujících částech s existujícími implementacemi rozhraní .NET.

### <a name="net-core-vs-net-framework"></a>Jádro .NET vs. rozhraní .NET Framework

.NET byl poprvé oznámen společností Microsoft v roce 2000 a vyvinul se odtud. Rozhraní .NET Framework byla primární implementací rozhraní .NET produkovanou společností Microsoft během tohoto téměř dvoudesetiletí.

Hlavní rozdíly mezi rozhraními .NET Core a .NET Framework jsou:

- **Modely aplikací** -- .NET Core nepodporuje všechny modely aplikací rozhraní .NET Framework. Zejména nepodporuje ASP.NET webových formulářů a ASP.NET MVC, ale podporuje ASP.NET Core MVC. A počínaje .NET Core 3.0, .NET Core také podporuje WPF a Windows Forms pouze v systému Windows.
- **Rozhraní API** -- .NET Core obsahuje velkou podmnožinu knihovny základních tříd rozhraní .NET Framework s jiným faktoringem (názvy sestavení se liší; členy vystavené na typy se liší v klíčových případech). V některých případech tyto rozdíly vyžadují změny zdroje portu na .NET Core. Další informace naleznete [v tématu .NET Portability Analyzer](../standard/analyzers/portability-analyzer.md). Jádro .NET implementuje specifikaci [rozhraní .NET Standard](../standard/net-standard.md) API.
- **Subsystémy** -- .NET Core implementují podmnožinu subsystémů v rozhraní .NET Framework s cílem jednoduššího implementačního a programovacího modelu. Například zabezpečení přístupu kódu (CAS) není podporováno, zatímco reflexe je podporována.
- **Platformy** -- .NET Framework podporují Windows a Windows Server, zatímco .NET Core také podporuje macOS a Linux.
- **Open source** -- .NET Core je open source, zatímco [podmnožina rozhraní .NET Framework jen pro čtení](https://github.com/microsoft/referencesource) je open source.

Zatímco .NET Core je jedinečný a má významné rozdíly v rozhraní .NET Framework a další implementace .NET, je jednoduché sdílet kód mezi těmito implementacemi pomocí zdrojových nebo binárních technik sdílení.

Vzhledem k tomu, že rozhraní .NET Core podporuje souběžnou instalaci a jeho runtime je zcela nezávislý na rozhraní .NET Framework, lze jej nainstalovat do počítačů s rozhraním .NET Framework nainstalovaným bez problémů.

### <a name="net-core-vs-mono"></a>.NET Jádro vs. Mono

[Mono](https://www.mono-project.com/) je původní implementace napříč platformami .NET. Začalo to jako [open source](https://github.com/mono/mono) alternativa k rozhraní .NET Framework a přešlo na cílení na mobilní zařízení, protože zařízení iOS a Android se stala populární. To si lze myslet jako společenství klon .NET Framework. Aby bylo zajištěno kompatibilní implementace, projektový tým Mono se spoléhal na otevřené [standardy .NET](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) (zejména ECMA 335) vydané společností Microsoft.

Hlavní rozdíly mezi .NET Core a Mono jsou:

- **Modely aplikací** -- Mono podporuje podmnožinu modelů aplikací rozhraní .NET Framework (například Windows Forms) a některé další pro vývoj mobilních zařízení (například [Xamarin.iOS)](https://www.xamarin.com/platform)prostřednictvím produktu Xamarin. .NET Core nepodporuje Xamarin.
- **Rozhraní API --** Mono podporuje [velkou podmnožinu](http://docs.go-mono.com/?link=root%3a%2fclasslib) rozhraní API rozhraní .NET Framework pomocí stejných názvů sestavení a faktoringu.
- **Platformy** -- Mono podporuje mnoho platforem a procesorů.
- **Open Source** -- Mono a .NET Core používají licenci MIT a jsou projekty .NET Foundation.
- **Focus** – Primární zaměření Mono v posledních letech je mobilní platformy, zatímco .NET Core se zaměřuje na cloudové a desktopové úlohy.

## <a name="support"></a>Podpora

.NET Core je [podporován společností Microsoft](https://dotnet.microsoft.com/platform/support/policy) v systémech Windows, macOS a Linux. Je pravidelně aktualizován z bezpečnostních důvodů (druhé úterý v měsíci).

Binární distribuce .NET Core od Microsoftu jsou sestavené a testované na serverech spravovaných společností Microsoft v Azure a postupujte podle technických a bezpečnostních postupů Microsoftu.

[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat staví .NET Core ze zdroje a zpřístupňuje jej v [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat a Microsoft spolupracují, aby zajistily, že .NET Core funguje dobře na RHEL.

[Tizen podporuje .NET Core](https://developer.tizen.org/development/training/.net-application) na platformách Tizen.
