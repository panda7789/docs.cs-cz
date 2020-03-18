---
title: Analyzátor přenosové možnosti rozhraní .NET - .NET
description: Naučte se používat nástroj .NET Portability Analyzer k vyhodnocení, jak přenosný je váš kód mezi různými implementacemi rozhraní .NET, včetně .NET Core, .NET Standard, UPW a Xamarin.
ms.date: 09/13/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: e0a5c791926b36fe5a35c5446471c3dcdb75cd7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72774381"
---
# <a name="the-net-portability-analyzer"></a>Analyzátor přenosové možnosti rozhraní .NET

Chcete, aby vaše knihovny podporovaly více platforem? Chcete zjistit, kolik práce je potřeba k tomu, aby byla aplikace rozhraní .NET Framework spuštěna na jádru .NET? [Nástroj .NET Portability Analyzer](https://github.com/microsoft/dotnet-apiport) je nástroj, který analyzuje sestavení a poskytuje podrobnou zprávu o rozhraníCH API rozhraní .NET, která chybí pro aplikace nebo knihovny, které mají být přenosné na určených cílených platformách .NET. Analyzátor přenositelnosti je nabízen jako [rozšíření sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), které analyzuje jedno sestavení na projekt, a jako [konzolová aplikace ApiPort](https://aka.ms/apiportdownload), která analyzuje sestavení podle zadaných souborů nebo adresářů.

Po převodu projektu na cílnovou platformu, jako je .NET Core, můžete použít [nástroj Analyzátor rozhraní](api-analyzer.md) API <xref:System.PlatformNotSupportedException> založený na Roslynu k identifikaci rozhraní API, která vyvolání výjimek a dalších problémů s kompatibilitou.

## <a name="common-targets"></a>Společné cíle

- [.NET Core](../../core/index.md): Má modulární návrh, zaměstnává vedle sebe a zaměřuje se na scénáře napříč platformami. Vedle sebe umožňuje přijmout nové verze .NET Core bez přerušení jiných aplikací. Pokud je vaším cílem přenést aplikaci na rozhraní .NET Core podporující různé platformy, je to doporučený cíl.
- . [NET Standard](../../standard/net-standard.md): Zahrnuje rozhraní API standardu .NET, která jsou k dispozici ve všech implementacích rozhraní .NET. Pokud je vaším cílem, aby vaše knihovna běžet na všech platformách podporovaných rozhraním .NET, je to doporučeno cíl.
- [ASP.NET Core](/aspnet/core): Moderní webový rámec postavený na .NET Core. Pokud je vaším cílem přenést webovou aplikaci do služby .NET Core pro podporu více platforem, je to doporučený cíl.
- Rozšíření .NET Core + [Platform Extensions](../../core/porting/windows-compat-pack.md): Kromě sady Windows Compatibility Pack obsahuje rozhraní .NET Core API, která poskytuje mnoho dostupných technologií rozhraní .NET Framework. Toto je doporučený cíl pro přenesení aplikace z rozhraní .NET Framework do .NET Core ve Windows.
- .NET Standard + [Rozšíření platformy](../../core/porting/windows-compat-pack.md): Zahrnuje rozhraní .NET Standard API kromě sady Windows Compatibility Pack, která poskytuje mnoho dostupných technologií rozhraní .NET Framework. Toto je doporučený cíl pro přenesení knihovny z rozhraní .NET Framework do rozhraní .NET Core v systému Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Použití analyzátoru přenosové schopnosti rozhraní .NET

Chcete-li začít používat nástroj .NET Portability Analyzer v sadě Visual Studio, musíte nejprve stáhnout a nainstalovat rozšíření z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Funguje v visual studiu 2017 a novějších verzích. Můžete ji nakonfigurovat v sadě Visual Studio pomocí **nástroje Analyzovat** > **nastavení analyzátoru přenositelnosti** a vybrat cílové platformy, což jsou platformy/verze rozhraní .NET, které chcete vyhodnotit mezery přenositelnosti ve srovnání s platformou nebo verzí, se kterou je vytvořeno aktuální sestavení.

![Snímek obrazovky analyzátoru přenositelnosti](./media/portability-analyzer/portability-screenshot.png)

Můžete také použít aplikaci konzoly ApiPort, stáhnout ji z [úložiště ApiPort](https://aka.ms/apiportdownload). Můžete použít `listTargets` možnost příkazu k zobrazení dostupného cílového `-t` seznamu `--target` a pak vybrat cílové platformy zadáním nebo možností příkazu.

### <a name="analyze-portability"></a>Analyzovat přenositelnost
Chcete-li analyzovat celý projekt v sadě Visual Studio, klikněte pravým tlačítkem myši na projekt v **Průzkumníkovi řešení** a vyberte **analyzovat přenositelnost sestavení**. V opačném případě přejděte do nabídky **Analyzovat** a vyberte **analyzovat přenositelnost sestavení**. Odtud vyberte spustitelný soubor projektu nebo dll.

![Snímek obrazovky s analyzátorem přenositelnosti z Průzkumníka řešení](./media/portability-analyzer/portability-solution-explorer.png)

Můžete také použít [konzolovou aplikaci ApiPort](https://aka.ms/apiportdownload).

- Zadejte následující příkaz pro analýzu aktuálního adresáře:`ApiPort.exe analyze -f .`
- Chcete-li analyzovat konkrétní seznam souborů DLL, zadejte následující příkaz:`ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
- Spusťte `ApiPort.exe -?` další pomoc

Doporučujeme zahrnout všechny související soubory exe a dll, které vlastníte a chcete je portovat, a vyloučit soubory, na kterých vaše aplikace závisí, ale nevlastníte a nemůžete je přenést. To vám poskytne nejrelevantnější zprávu o přenositelnosti.

### <a name="view-and-interpret-portability-result"></a>Zobrazit a interpretovat výsledek přenositelnosti

V sestavě se zobrazí pouze řešení API, která nejsou podporována cílovou platformou.
Po spuštění analýzy v sadě Visual Studio se zobrazí odkaz na soubor sestavy přenositelnost rozhraní .NET. Pokud jste [použili konzolovou aplikaci ApiPort](https://aka.ms/apiportdownload), bude sestava přenositelnost rozhraní .NET uložena jako soubor v určeném formátu. Výchozí hodnota je v souboru aplikace Excel (*xlsx*) v aktuálním adresáři.

#### <a name="portability-summary"></a>Souhrn přenositelnosti

![Snímek obrazovky se souhrnem přenositelnosti](./media/portability-analyzer/api-catalog-portablility-summary.png)

Část Souhrn přenositelnosti v sestavě zobrazuje procento přenositelnosti pro každé sestavení zahrnuté do běhu. V předchozím příkladu 71.24 % rozhraní API rozhraní `svcutil` .NET Framework používaných v aplikaci je k dispozici v rozšířeních .NET Core + Platform Extensions. Pokud spustíte nástroj .NET Přenositelnost Analyzer proti více sestavení, každé sestavení by měl mít řádek v sestavě přenositelnost souhrnu.

#### <a name="details"></a>Podrobnosti

![Snímek obrazovky s podrobnostmi o přenositelnosti](./media/portability-analyzer/api-catalog-portablility-details.png)

V části **Podrobnosti** v sestavě jsou uvedena chybějící api na některé z vybraných **cílových platforem**.

- Typ cíle: v typu chybí rozhraní API z cílové platformy.
- Cílový člen: metoda chybí v cílové platformě
- Název sestavení: sestavení rozhraní .NET Framework, ve které se v rozhraní API nese.
- Každá z vybraných cílových platforem je jeden sloupec, například ".NET Core": "Není podporováno" hodnota znamená, že rozhraní API není podporováno na této cílové platformě.
- Doporučené změny: doporučené rozhraní API nebo technologie, na které se má změnit. V současné době je toto pole prázdné nebo zastaralé pro velké množství řešení API. Vzhledem k velkému počtu api, máme velkou výzvu, aby to. Hledáme alternativní řešení, která zákazníkům poskytnou užitečné informace.

#### <a name="missing-assemblies"></a>Chybějící sestavení

![Snímek obrazovky s chybějícími sestaveními](./media/portability-analyzer/api-catalog-missing-assemblies.png)

Část Chybějící sestavení najdete v sestavě. Informuje vás, že tento seznam sestavení jsou odkazovány analyzované sestavení a nebyly analyzovány. Pokud se jedná o sestavení, které vlastníte, zahrňte jej do analyzátoru přenositelnosti rozhraní API, abyste pro něj mohli získat podrobnou sestavu přenositelnosti na úrovni rozhraní API. Pokud se jedná o knihovnu třetích stran, vyhledá, pokud mají novější verzi podporující vaši cílovou platformu. Pokud ano, zvažte přechod na novější verzi. Nakonec byste očekávali, že tento seznam obsahuje všechna sestavení třetích stran, na kterých vaše aplikace závisí, a potvrdil, že mají verzi podporující vaši cílovou platformu.

Další informace o nástroji .NET Portability Analyzer najdete v [dokumentaci k GitHubu](https://github.com/Microsoft/dotnet-apiport#documentation) a [stručný přehled videa .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9.
