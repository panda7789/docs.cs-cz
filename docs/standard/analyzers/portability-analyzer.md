---
title: .NET Portability Analyzeru – .NET
description: Další informace o použití nástroje .NET Portability Analyzeru vyhodnotit, jak přenosné váš kód je mezi různé implementace .NET, včetně .NET Core, .NET Standard, UPW a Xamarin.
ms.date: 07/10/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 73a9cacbce02880d236f87459673812af9828916
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238547"
---
# <a name="the-net-portability-analyzer"></a>.NET Portability Analyzeru

Chcete si vytvořit svoje knihovny podporují více platforem? Chcete zobrazit, kolik práce je nutná, aby vaše aplikace kompatibilní s jinými implementace .NET a profily, včetně .NET Core, .NET Standard, UPW a Xamarin pro iOS, Android a Mac? [.NET Portability Analyzeru](https://github.com/microsoft/dotnet-apiport) je nástroj, který vám poskytne podrobnou zprávu o jak flexibilní program je implementace .NET díky analýze sestavení. Analyzátor přenositelnosti se nabízí jako [rozšíření sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), který analyzuje sestavení na projekt a jako [ApiPort konzolovou aplikaci](https://aka.ms/apiportdownload), který analyzuje sestavení podle určité soubory nebo adresáře.

## <a name="common-targets"></a>Společné cíle

* [.NET Core](../../core/index.md): Má modulárního návrhu, využívá vedle sebe a cílí na scénáře napříč platformami. Vedle sebe umožňuje přijmout nové verze .NET Core bez porušení dalších aplikací. Pokud je vaším cílem je portovat svou aplikaci až po .NET Core podporující různé platformy, toto je doporučené cíl. 
* . [.NET Standard](../../standard/net-standard.md): Zahrnuje standardní rozhraní API .NET k dispozici na všech implementace .NET. Pokud je vaším cílem je, aby vaši knihovnu běží na rozhraní .NET všechny podporované platformy, to se doporučuje cíl.  
* [ASP.NET Core](/aspnet/core): Moderní webové rozhraní založená na prostředí .NET Core. Pokud je vaším cílem je port webové aplikace až po .NET Core pro podporu více platforem, toto je doporučená cíl.
* .NET core + [rozšíření platformy](../../core/porting/windows-compat-pack.md): Zahrnuje rozhraní API .NET Core kromě sady Windows Compatibility Pack, které poskytuje řadu dostupných technologií rozhraní .NET Framework. Toto je doporučená cíl pro přenesení aplikace z rozhraní .NET Framework do .NET Core ve Windows.
* .NET standard + [rozšíření platformy](../../core/porting/windows-compat-pack.md): Zahrnuje standardní rozhraní API .NET kromě sady Windows Compatibility Pack, které poskytuje řadu dostupných technologií rozhraní .NET Framework. Toto je doporučená cíl pro přenos knihovny z rozhraní .NET Framework do .NET Core ve Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Jak používat .NET Portability Analyzeru

Pokud chcete začít používat .NET Portability Analyzeru v sadě Visual Studio, musíte nejprve stáhnout a nainstalovat rozšíření z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Funguje ve Visual Studio 2017 a novějších verzích. Můžete vytvořit v sadě Visual Studio prostřednictvím **analyzovat** > **nastavení analyzátor přenositelnosti** a vyberte cílové platformy, která je na platformy a verze rozhraní .NET, které chcete vyhodnotit Výsledkem porovnání s platformě, verzi, která vaše aktuální sestavení je integrovaná s přenositelností mezery.

![Snímek obrazovky s přenositelností](./media/portability-analyzer/portability-screenshot.png)

Můžete použít také ApiPort konzolovou aplikaci, si ji stáhnout z [ApiPort úložiště](http://aka.ms/apiportdownload). Můžete použít `listTargets` možnost pro zobrazení seznamu dostupných cílů, a pak vyberte cílové platformy zadáním příkazu `-t` nebo `--target` možnost příkazu. 

### <a name="analyze-portability"></a>Analýza přenositelnosti
Pokud chcete analyzovat celý projekt v sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **analyzovat přenositelnost sestavení**. V opačném případě přejděte **analyzovat** nabídky a vybereme **analyzovat přenositelnost sestavení**. Tam pak vyberete spustitelný soubor projektu nebo knihovny DLL.

![Analyzátor přenositelnosti z Průzkumníka řešení](./media/portability-analyzer/portability-solution-explorer.png)

Můžete také použít [ApiPort konzolovou aplikaci](https://aka.ms/apiportdownload). 

* Zadejte následující příkaz, který analýza aktuálním adresáři: `ApiPort.exe analyze -f .`
* Pokud chcete analyzovat konkrétního seznamu souborů DLL, zadejte následující příkaz: `ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
* Spustit `ApiPort.exe -?` můžete získat další nápovědu

Doporučuje se, že složku zahrnujete všechny související exe a dll soubory, které vlastníte a port, a vyloučit soubory, které vaše aplikace závisí, ale není vlastníkem a nelze přenést. Tím získáte relevantní přenositelnost sestavy.  

### <a name="view-and-interpret-portability-result"></a>Zobrazení a interpretace výsledků přenositelnosti

V sestavě se zobrazují pouze rozhraní API, které jsou nepodporuje cílovou platformu. Po spuštění analýzy v sadě Visual Studio, uvidíte, že se že zobrazí odkaz na soubor sestavy .NET přenositelnost. Pokud jste použili [ApiPort konzolovou aplikaci](https://aka.ms/apiportdownload), .NET Portability sestavy je uložen jako soubor ve formátu, který jste zadali. Výchozí hodnota je v Excelovém souboru ( *.xlsx*) v aktuálním adresáři.

#### <a name="portability-summary"></a>Souhrn přenositelnosti 

![Souhrn přenositelnosti](./media/portability-analyzer/portabilitysummary.png)

Souhrn přenositelnost část sestavy zobrazuje procento přenositelnost pro každé sestavení součástí běhu. V předchozím příkladu 89.74 % API rozhraní .NET Framework používáno `ConsoleAppFramework` aplikace jsou k dispozici v .NET Core + v2.2 rozšíření platformy. Pokud spustíte nástroj .NET Portability Analyzeru proti více sestavení, každé sestavení by měl obsahovat řádek v sestavě Souhrn přenositelnost.

#### <a name="details"></a>Podrobnosti

![Podrobnosti o přenositelnosti](./media/portability-analyzer/portabilitydetails.png)

Podrobnosti o části sestavy je uveden seznam, chybí rozhraní API z jednoho z cílové platformy. 

- Cílový typ: typ chybí rozhraní API z cílové platformy 
- Cílový člen: metoda chybí Cílová platforma 
- Název sestavení: sestavení rozhraní .NET Framework, která se chybějící rozhraní API nachází. 
- Každý z vybraných cílových platforem je jeden sloupec, jako je například ".NET Core": Hodnota "Nepodporuje" znamená, že tato Cílová platforma nepodporuje rozhraní API. 
- Doporučuje změny: doporučená rozhraní API nebo technologie změnit. V současné době toto pole je prázdné nebo zastaralá spoustu rozhraní API. Z důvodu velkého počtu rozhraní API máme velké objemy obtížné udržovat tempo. Těšíme se na alternativní řešení zákazníkům poskytovat užitečné informace.

#### <a name="missing-assemblies"></a>Chybějící sestavení

![Podrobnosti o přenositelnosti](./media/portability-analyzer/missingassemblies.png)

V sestavě můžete zjistit oddílu chybějící sestavení. Zjistíte, že tento seznam sestavení je odkazováno dle analyzované sestavení a se neanalyzovaly. Pokud je sestavení, které vlastníte, můžete jej zahrnout do portability analyzeru Api spustit tak, aby rozhraní API úrovně přenositelnost podrobné sestavy můžete získat pro ni. Pokud je knihovny třetích stran, hledá Pokud mají novější verze podporuje vaši cílovou platformu. V takovém případě zvažte přechod na novější verzi. Nakonec byste očekávali, že tento seznam obsahuje všechna sestavení třetích stran, které vaše aplikace závisí na a potvrdit, že mají na verzi podporující cílovou platformu.  

Další informace o .NET Portability Analyzeru najdete [dokumentaci na Githubu](https://github.com/Microsoft/dotnet-apiport#documentation) a [A stručný podívejte se na .NET Portability Analyzeru](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) videa Channel 9.
