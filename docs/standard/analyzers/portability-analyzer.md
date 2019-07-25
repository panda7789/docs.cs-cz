---
title: Analyzátor přenositelnosti .NET – .NET
description: Naučte se používat nástroj Analyzátor přenositelnosti .NET k vyhodnocení způsobu, jakým je přenos kódu mezi různými implementacemi .NET, včetně .NET Core, .NET Standard, UWP a Xamarin.
ms.date: 07/18/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 32b4f980061b0975c413a8cde436074f76cfabc9
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433942"
---
# <a name="the-net-portability-analyzer"></a>Analyzátor přenositelnosti .NET

Chcete, aby vaše knihovny podporovaly více platforem? Chcete zjistit, kolik práce je potřeba k zajištění kompatibility vaší aplikace s jinými implementacemi a profily .NET, včetně .NET Core, .NET Standard, UWP a Xamarin pro iOS, Android a Mac? [Analyzátor přenositelnosti .NET](https://github.com/microsoft/dotnet-apiport) je nástroj, který vám poskytne podrobnou zprávu o tom, jak flexibilní je program napříč implementacemi .NET analýzou sestavení. Analyzátor přenositelnosti se nabízí jako [rozšíření sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), které analyzuje sestavení na projekt a jako konzolovou [aplikaci ApiPort](https://aka.ms/apiportdownload), která analyzuje sestavení podle zadaných souborů nebo adresáře.

## <a name="common-targets"></a>Společné cíle

* [.NET Core](../../core/index.md): Má modulární návrh, který využívá souběžné a cílené scénáře pro různé platformy. Vedle sebe vám umožní přijmout nové verze .NET Core bez porušení dalších aplikací. Pokud je vaším cílem, aby vaše aplikace podporovala více platforem .NET Core, jedná se o doporučený cíl. 
* . [NET Standard](../../standard/net-standard.md): Zahrnuje rozhraní API .NET Standard dostupná pro všechny implementace rozhraní .NET. Pokud vaším cílem je, aby se vaše knihovna spouštěla na všech platformách podporovaných rozhraním .NET, je to doporučený cíl.  
* [ASP.NET Core](/aspnet/core): Moderní webové rozhraní postavené na .NET Core. Pokud je vaším cílem, aby vaše webová aplikace podporovala více platforem na .NET Core, jedná se o doporučený cíl.
* Rozšíření .NET Core + [Platform](../../core/porting/windows-compat-pack.md): Zahrnuje rozhraní API .NET Core kromě sady Windows Compatibility Pack, která poskytuje mnoho dostupných technologií .NET Framework. Toto je doporučený cíl pro přenos vaší aplikace z .NET Framework do .NET Core ve Windows.
* Rozšíření .NET Standard + [platforma](../../core/porting/windows-compat-pack.md): Zahrnuje .NET Standard rozhraní API kromě sady Windows Compatibility Pack, která poskytuje mnoho dostupných technologií .NET Framework. Toto je doporučený cíl pro přenos knihovny z .NET Framework do .NET Core ve Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Jak používat analyzátor přenositelnosti .NET

Pokud chcete začít používat analyzátor přenositelnosti .NET v aplikaci Visual Studio, musíte nejdřív stáhnout a nainstalovat rozšíření z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Funguje v sadě Visual Studio 2017 a novějších verzích. Můžete ji nakonfigurovat v aplikaci Visual Studio prostřednictvím možnosti **Analýza** > **Nastavení analyzátoru přenositelnosti** a vybrat cílové platformy, což je platforma nebo verze .NET, pro které chcete vyhodnotit mezery na přenositelnosti porovnávání s platformou/ verze, pomocí které je vytvořeno vaše aktuální sestavení.

![Snímek obrazovky přenositelnosti](./media/portability-analyzer/portability-screenshot.png)

Můžete také použít konzolovou aplikaci ApiPort, kterou si můžete stáhnout z [úložiště ApiPort](https://aka.ms/apiportdownload). Pomocí `listTargets` možnosti příkaz můžete zobrazit dostupný cílový seznam a pak vybrat cílové platformy zadáním `-t` možnosti nebo `--target` pomocí příkazu. 

### <a name="analyze-portability"></a>Analýza přenositelnosti
Chcete-li analyzovat celý projekt v aplikaci Visual Studio, klikněte pravým tlačítkem myši na projekt v **Průzkumník řešení** a vyberte možnost **analyzovat přenositelnost sestavení**. V opačném případě přejděte do nabídky **analyzovat** a vyberte možnost **analyzovat přenositelnost sestavení**. Odtud vyberte spustitelný soubor nebo knihovnu DLL vašeho projektu.

![Analyzátor přenositelnosti z Průzkumník řešení](./media/portability-analyzer/portability-solution-explorer.png)

Můžete také použít konzolovou [aplikaci ApiPort](https://aka.ms/apiportdownload). 

* Chcete-li analyzovat aktuální adresář, zadejte následující příkaz:`ApiPort.exe analyze -f .`
* Chcete-li analyzovat konkrétní seznam souborů. dll, zadejte následující příkaz:`ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
* Spusťte `ApiPort.exe -?` , abyste získali další nápovědu.

Doporučujeme, abyste zahrnuli všechny související soubory exe a DLL, které vlastníte a chcete portovat, a vyloučíte soubory, na kterých vaše aplikace závisí, ale nevlastníte a nemůžete port. Tím získáte nejvíc relevantní sestavu přenositelnosti.  

### <a name="view-and-interpret-portability-result"></a>Zobrazit a interpretovat výsledek přenositelnosti

V sestavě se zobrazí pouze rozhraní API, která nejsou v cílové platformě podporována. Po spuštění analýzy v aplikaci Visual Studio se zobrazí odkaz na soubor sestavy přenositelnosti .NET. Pokud jste použili [konzolovou aplikaci ApiPort](https://aka.ms/apiportdownload), vaše sestava přenositelnosti .NET se uloží jako soubor ve formátu, který jste zadali. Výchozí hodnota je v souboru aplikace Excel ( *. xlsx*) ve vašem aktuálním adresáři.

#### <a name="portability-summary"></a>Souhrn přenositelnosti 

![Souhrn přenositelnosti](./media/portability-analyzer/portabilitysummary.png)

V části Souhrn přenositelnosti sestavy se zobrazuje procento přenositelnosti pro každé sestavení zahrnuté v běhu. V předchozím příkladu je 71,24% .NET Framework rozhraní API používaných v `svcutil` aplikaci dostupné v rozšířeních .NET Core + Platform. Pokud spustíte nástroj Analyzátor přenositelnosti .NET pro více sestavení, musí mít každé sestavení řádek v sestavě souhrn přenositelnosti.

#### <a name="details"></a>Podrobnosti

![Podrobnosti přenositelnosti](./media/portability-analyzer/portabilitydetails.png)

Část podrobnosti sestavy obsahuje seznam rozhraní API chybějících z jedné z cílových platforem. 

- Cílový typ: typ má chybějící rozhraní API z cílové platformy. 
- Cílový člen: v cílové platformě chybí metoda. 
- Název sestavení: .NET Framework sestavení, ve kterém chybí rozhraní API. 
- Každá z vybraných cílových platforem je jedním sloupcem, například ".NET Core": Hodnota Nepodporováno znamená, že rozhraní API není na této cílové platformě podporováno. 
- Doporučené změny: Doporučené rozhraní API nebo technologie se změní na. V současné době je toto pole prázdné nebo zastaralé pro spoustu rozhraní API. Vzhledem k velkému počtu rozhraní API máme velkou výzvu, abychom ji zachovali. Těšíme se na alternativní řešení, abychom zákazníkům poskytli užitečné informace.

#### <a name="missing-assemblies"></a>Chybějící sestavení

![Podrobnosti přenositelnosti](./media/portability-analyzer/missingassemblies.png)

V sestavě můžete najít část chybějící sestavení. Oznamuje vám, že se na tento seznam sestavení odkazuje vaše analyzovaná sestavení a že nebyly analyzovány. Pokud se jedná o sestavení, které vlastníte, zahrňte ho do spuštění analyzátoru přenositelnosti rozhraní API, abyste pro něj mohli získat podrobnou sestavu přenositelnosti rozhraní API. Pokud se jedná o knihovnu třetích stran, vyhledá, jestli má novější verzi podporující cílovou platformu. V takovém případě zvažte přechod na novější verzi. Nakonec byste očekávali, že tento seznam zahrnuje všechna sestavení třetích stran, na kterých vaše aplikace závisí, a potvrzuje, že mají verzi podporující cílovou platformu.  

Další informace o analyzátoru přenositelnosti .NET najdete v [dokumentaci k GitHubu](https://github.com/Microsoft/dotnet-apiport#documentation) a na krátkém pohledu na video [o analyzátoru přenositelnosti .NET pro](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) kanál 9.
