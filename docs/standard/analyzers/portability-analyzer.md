---
title: Analyzátor přenositelnosti .NET – .NET
description: Naučte se používat nástroj Analyzátor přenositelnosti .NET k vyhodnocení způsobu, jakým je přenos kódu mezi různými implementacemi .NET, včetně .NET Core, .NET Standard, UWP a Xamarin.
ms.date: 09/13/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: a3979d792b4cfd1f7949a3c8e14c6f856e9e3e21
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320115"
---
# <a name="the-net-portability-analyzer"></a>Analyzátor přenositelnosti .NET

Chcete, aby vaše knihovny podporovaly více platforem? Chcete zjistit, kolik práce je potřeba, aby vaše aplikace .NET Framework běžela v .NET Core?  [Analyzátor přenositelnosti .NET](https://github.com/microsoft/dotnet-apiport) je nástroj, který vám poskytne podrobnou zprávu o chybějících rozhraních API .NET pro vaše aplikace nebo knihovny pro přenos na zadané cílené platformy .NET analýzou sestavení. Analyzátor přenositelnosti se nabízí jako [rozšíření sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), které analyzuje sestavení na projekt a jako [konzolovou aplikaci ApiPort](https://aka.ms/apiportdownload), která analyzuje sestavení podle zadaných souborů nebo adresáře.

Jakmile váš projekt převedete na cílení na cílovou platformu, jako je například .NET Core, můžete použít Roslyn založený na nástroji [API Analyzer Tool] ([https://docs.microsoft.com/en-us/dotnet/standard/analyzers/api-analyzer](api-analyzer.md) pro identifikaci rozhraní API pro vyvolání PlatformNotSupportedException a některé jiné problémy s kompatibilitou.

## <a name="common-targets"></a>Společné cíle

- [.NET Core](../../core/index.md): má modulární návrh, který využívá souběžné a cílené scénáře pro různé platformy. Vedle sebe vám umožní přijmout nové verze .NET Core bez porušení dalších aplikací. Pokud je vaším cílem, aby vaše aplikace podporovala více platforem .NET Core, jedná se o doporučený cíl. 
- . [NET Standard](../../standard/net-standard.md): zahrnuje rozhraní api pro .NET Standard dostupná ve všech implementacích .NET. Pokud vaším cílem je, aby se vaše knihovna spouštěla na všech platformách podporovaných rozhraním .NET, je to doporučený cíl.  
- [ASP.NET Core](/aspnet/core): moderní webové rozhraní postavené na .NET Core. Pokud je vaším cílem, aby vaše webová aplikace podporovala více platforem na .NET Core, jedná se o doporučený cíl.
- Rozšíření .NET Core + [Platform](../../core/porting/windows-compat-pack.md): Kromě sady Windows Compatibility Pack obsahuje rozhraní API .NET Core, které poskytuje mnoho dostupných technologií .NET Framework. Toto je doporučený cíl pro přenos vaší aplikace z .NET Framework do .NET Core ve Windows.
- Rozšíření .NET Standard + [platforma](../../core/porting/windows-compat-pack.md): Kromě sady Windows Compatibility Pack zahrnuje i rozhraní API .NET Standard, která poskytují mnoho dostupných technologií .NET Framework. Toto je doporučený cíl pro přenos knihovny z .NET Framework do .NET Core ve Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Jak používat analyzátor přenositelnosti .NET

Pokud chcete začít používat analyzátor přenositelnosti .NET v aplikaci Visual Studio, musíte nejdřív stáhnout a nainstalovat rozšíření z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Funguje v sadě Visual Studio 2017 a novějších verzích. Můžete ji nakonfigurovat v aplikaci Visual Studio pomocí možnosti **analyzovat**@no__t – 1**Nastavení analyzátoru přenositelnosti** a vybrat cílové platformy, což jsou platformy .NET/verze, u kterých chcete vyhodnotit přenositelnost mezer při porovnávání s platformou/ verze, pomocí které je vytvořeno vaše aktuální sestavení.

![Snímek obrazovky s analyzátorem přenositelnosti](./media/portability-analyzer/portability-screenshot.png)

Můžete také použít konzolovou aplikaci ApiPort, kterou si můžete stáhnout z [úložiště ApiPort](https://aka.ms/apiportdownload). Pomocí možnosti příkazového řádku `listTargets` můžete zobrazit dostupný cílový seznam a pak vybrat cílové platformy zadáním možnosti příkazového řádku `-t` nebo `--target`. 

### <a name="analyze-portability"></a>Analýza přenositelnosti
Chcete-li analyzovat celý projekt v aplikaci Visual Studio, klikněte pravým tlačítkem myši na projekt v **Průzkumník řešení** a vyberte možnost **analyzovat přenositelnost sestavení**. V opačném případě přejděte do nabídky **analyzovat** a vyberte možnost **analyzovat přenositelnost sestavení**. Odtud vyberte spustitelný soubor nebo knihovnu DLL vašeho projektu.

![Snímek obrazovky analyzátoru přenositelnosti z Průzkumník řešení.](./media/portability-analyzer/portability-solution-explorer.png)

Můžete také použít [konzolovou aplikaci ApiPort](https://aka.ms/apiportdownload). 

- Zadáním následujícího příkazu Analyzujte aktuální adresář: `ApiPort.exe analyze -f .`
- Chcete-li analyzovat konkrétní seznam souborů. dll, zadejte následující příkaz: `ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
- Pokud chcete získat další nápovědu, spusťte `ApiPort.exe -?`.

Doporučujeme, abyste zahrnuli všechny související soubory exe a DLL, které vlastníte a chcete portovat, a vyloučíte soubory, na kterých vaše aplikace závisí, ale nevlastníte a nemůžete port. Tím získáte nejvíc relevantní sestavu přenositelnosti.  

### <a name="view-and-interpret-portability-result"></a>Zobrazit a interpretovat výsledek přenositelnosti

V sestavě se zobrazí pouze rozhraní API, která nejsou v cílové platformě podporována. Po spuštění analýzy v aplikaci Visual Studio se zobrazí odkaz na soubor sestavy přenositelnosti .NET. Pokud jste použili [konzolovou aplikaci ApiPort](https://aka.ms/apiportdownload), vaše sestava přenositelnosti .NET se uloží jako soubor ve formátu, který jste zadali. Výchozí hodnota je v souboru aplikace Excel ( *. xlsx*) ve vašem aktuálním adresáři.

#### <a name="portability-summary"></a>Souhrn přenositelnosti 

![Snímek obrazovky souhrnu přenositelnosti](./media/portability-analyzer/api-catalog-portablility-summary.png)

V části Souhrn přenositelnosti sestavy se zobrazuje procento přenositelnosti pro každé sestavení zahrnuté v běhu. V předchozím příkladu je 71,24% .NET Framework rozhraní API používaných v aplikaci `svcutil` k dispozici v rozšířeních .NET Core + Platform. Pokud spustíte nástroj Analyzátor přenositelnosti .NET pro více sestavení, musí mít každé sestavení řádek v sestavě souhrn přenositelnosti.

#### <a name="details"></a>Podrobnosti

![Snímek obrazovky s podrobnostmi o přenositelnosti](./media/portability-analyzer/api-catalog-portablility-details.png)

V části **Podrobnosti** sestavy jsou uvedena chybějící rozhraní API ze všech vybraných **cílových platforem**. 

- Cílový typ: typ má chybějící rozhraní API z cílové platformy. 
- Cílový člen: v cílové platformě chybí metoda. 
- Název sestavení: .NET Framework sestavení, ve kterém chybí rozhraní API. 
- Každá z vybraných cílových platforem je jeden sloupec, jako je například hodnota ".NET Core": "Nepodporovaná" znamená, že rozhraní API není na této cílové platformě podporováno. 
- Doporučené změny: Doporučené rozhraní API nebo technologie se změní na. V současné době je toto pole prázdné nebo zastaralé pro spoustu rozhraní API. Vzhledem k velkému počtu rozhraní API máme velkou výzvu, abychom ji zachovali. Těšíme se na alternativní řešení, abychom zákazníkům poskytli užitečné informace.

#### <a name="missing-assemblies"></a>Chybějící sestavení

![Snímek obrazovky s chybějícími sestaveními](./media/portability-analyzer/api-catalog-missing-assemblies.png)

V sestavě můžete najít část chybějící sestavení. Oznamuje vám, že se na tento seznam sestavení odkazuje vaše analyzovaná sestavení a že nebyly analyzovány. Pokud se jedná o sestavení, které vlastníte, zahrňte ho do spuštění analyzátoru přenositelnosti rozhraní API, abyste pro něj mohli získat podrobnou sestavu přenositelnosti rozhraní API. Pokud se jedná o knihovnu třetích stran, vyhledá, jestli má novější verzi podporující cílovou platformu. V takovém případě zvažte přechod na novější verzi. Nakonec byste očekávali, že tento seznam zahrnuje všechna sestavení třetích stran, na kterých vaše aplikace závisí, a potvrzuje, že mají verzi podporující cílovou platformu.  

Další informace o analyzátoru přenositelnosti .NET najdete v [dokumentaci k GitHubu](https://github.com/Microsoft/dotnet-apiport#documentation) a na [krátkém pohledu na video o analyzátoru přenositelnosti .NET pro](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) kanál 9.
