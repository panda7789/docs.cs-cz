---
title: Přehled doplňků WPF
ms.date: 03/30/2017
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
ms.openlocfilehash: 4fd8fe00fe6974bdcbf7b4af4da25150996de8c3
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401707"
---
# <a name="wpf-add-ins-overview"></a>Přehled doplňků WPF

<a name="Introduction"></a>.NET Framework obsahuje Model doplňku, který mohou vývojáři použít k vytváření aplikací podporujících rozšíření doplňku. Tento model doplňku umožňuje vytváření doplňků, které se integrují s funkcemi aplikace a rozšiřuje je. V některých scénářích aplikace také potřebují zobrazit uživatelská rozhraní, která jsou poskytována doplňky. V tomto tématu se dozvíte, jak WPF rozšiřuje .NET Framework Model doplňku, aby umožnil tyto scénáře, architekturu za ním, její výhody a omezení.

<a name="Requirements"></a>

## <a name="prerequisites"></a>Požadavky

Je požadována znalost .NET Framework Model doplňku. Další informace najdete v tématu [Doplňky a rozšiřitelnost](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="AddInsOverview"></a>

## <a name="add-ins-overview"></a>Přehled doplňků

Aby se zabránilo složitým sestavování a opětovnému nasazení aplikace za účelem zahrnutí nových funkcí, aplikace implementují mechanismy rozšíření, které umožňují vývojářům (první straně i třetí straně) vytvořit další aplikace, které Integrujte je s nimi. Nejběžnější způsob, jak tento typ rozšiřitelnosti podpořit, je použití doplňků (označovaných také jako doplňky a moduly plug-in). Příklady reálných aplikací, které zpřístupňují rozšiřitelnost s doplňky, zahrnují:

- Doplňky aplikace Internet Explorer.

- Moduly plug-in Windows Media Player.

- Doplňky sady Visual Studio.

Například model doplňku Windows Media Player umožňuje vývojářům třetích stran implementovat "moduly plug-in", které rozšíří Media Player Windows různým způsobem, včetně vytváření dekodérů a kodérů pro formáty médií, které Windows nepodporují nativně. Media Player (například DVD, MP3), zvukové efekty a vzhledy. Každý model doplňku je sestaven tak, aby vystavoval funkce, které jsou pro aplikaci jedinečné, i když existuje několik entit a chování, které jsou společné pro všechny modely doplňku.

Tři hlavní entity typických řešení rozšíření doplňku jsou *smlouvy*, *Doplňky*a *hostitelské aplikace*. Smlouvy definují, jak se doplňky integrují s hostitelskými aplikacemi dvěma způsoby:

- Doplňky jsou integrovány s funkcemi, které jsou implementovány hostitelskými aplikacemi.

- Hostitelské aplikace zpřístupňují funkce doplňků pro integraci s nástrojem.

Aby bylo možné použít doplňky, hostitelské aplikace je musí najít a načíst za běhu. V důsledku toho aplikace, které podporují doplňky, mají následující další zodpovědnosti:

- **Zjišťování**: Hledání doplňků, které odpovídají smlouvám podporovaným hostitelskými aplikacemi.

- **Aktivace**: Načítání, spouštění a navazování komunikace s doplňky.

- **Izolace**: Použití aplikačních domén nebo procesů k vytvoření hranic izolace, které chrání aplikace před potenciálními problémy zabezpečení a spouštění s doplňky.

- **Komunikace**: Povolení doplňků a hostitelských aplikací ke vzájemné komunikaci napříč hranicemi izolace voláním metod a předáváním dat.

- **Správa životnosti**: Načítání a uvolňování domén aplikací a procesů v čistém, předvídatelným způsobem (viz [domény aplikace](../../app-domains/application-domains.md)).

- **Správa verzí**: Zajistěte, aby hostitelské aplikace a doplňky i nadále komunikovaly při vytváření nových verzí obou.

Nakonec vývoj robustního modelu doplňku je netriviálním členem. Z tohoto důvodu .NET Framework poskytuje infrastrukturu pro sestavování modelů doplňku.

> [!NOTE]
> Podrobnější informace o doplňcích najdete v tématu [Doplňky a rozšiřitelnost](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="NETFrameworkAddInModelOverview"></a>

## <a name="net-framework-add-in-model-overview"></a>Přehled .NET Frameworkho modelu doplňku

.NET Framework Model doplňku nalezený v <xref:System.AddIn> oboru názvů obsahuje sadu typů, které jsou navrženy pro zjednodušení vývoje rozšíření doplňku. Základní jednotka .NET Frameworkho modelu doplňku je *kontrakt*, který definuje, jak hostitelská aplikace a doplněk vzájemně komunikují. Kontrakt se zveřejňuje pro hostitelskou aplikaci pomocí *zobrazení* smlouvy pro konkrétní hostitele. Podobně je *zobrazení* smlouvy pro konkrétní doplněk zpřístupněno doplňku. *Adaptér* se používá k tomu, aby hostitelská aplikace a doplněk komunikovaly mezi příslušnými zobrazeními smlouvy. Kontrakty, zobrazení a adaptéry se označují jako segmenty a sada souvisejících segmentů představuje *kanál*. Kanály jsou základem, na kterém .NET Framework Model doplňku podporuje zjišťování, aktivaci, izolaci zabezpečení, izolaci spouštění (pomocí domén a procesů aplikace), komunikace, správy životnosti a správu verzí.

Součet této podpory umožňuje vývojářům vytvářet doplňky, které se integrují s funkcemi hostitelské aplikace. Některé scénáře však vyžadují, aby aplikace hostitele zobrazovala uživatelská rozhraní poskytovaná doplňky. Vzhledem k tomu, že každá prezentační technologie v .NET Framework má svůj vlastní model pro implementaci uživatelských rozhraní, model .NET Framework doplňku nepodporuje žádnou konkrétní prezentační technologii. Místo toho WPF rozšiřuje model doplňku .NET Framework s podporou uživatelského rozhraní pro doplňky.

<a name="WPFAddInModel"></a>

## <a name="wpf-add-ins"></a>Doplňky WPF

WPF, ve spojení s modelem doplňku .NET Framework, umožňuje adresovat širokou škálu scénářů, které vyžadují, aby hostitelské aplikace zobrazovaly uživatelská rozhraní z doplňků. Konkrétně tyto scénáře řeší WPF pomocí následujících dvou programovacích modelů:

1. **Doplněk vrátí uživatelské rozhraní**. Doplněk vrací uživatelské rozhraní pro hostitelskou aplikaci prostřednictvím volání metody, jak je definováno ve smlouvě. Tento scénář se používá v následujících případech:

    - Vzhled uživatelského rozhraní vráceného doplňkem je závislý na datech nebo podmínkách, které existují pouze v době běhu, například v dynamicky generovaných sestavách.

    - Uživatelské rozhraní pro služby poskytované doplňkem se liší od uživatelského rozhraní hostitelských aplikací, které mohou doplněk použít.

    - Doplněk primárně provádí službu pro hostitelskou aplikaci a hlásí stav do hostitelské aplikace s uživatelským rozhraním.

2. **Doplněk je uživatelské rozhraní**. Doplněk je uživatelské rozhraní, jak je definováno smlouvou. Tento scénář se používá v následujících případech:

    - Doplněk neposkytuje služby, které nejsou zobrazené, jako je například reklama.

    - Uživatelské rozhraní pro služby poskytované doplňkem je společné pro všechny hostitelské aplikace, které mohou používat tento doplněk, jako je například Kalkulačka nebo výběr barvy.

Tyto scénáře vyžadují, aby objekty uživatelského rozhraní bylo možné předat mezi hostitelskou aplikací a doménami aplikace doplňku. Vzhledem k tomu, že model doplňku .NET Framework spoléhá na vzdálenou komunikaci mezi doménami aplikace, předávané objekty musí být vzdáleně.

Vzdáleně přidaný objekt je instancí třídy, která provádí jednu nebo více následujících akcí:

- Je odvozen z <xref:System.MarshalByRefObject> třídy.

- <xref:System.Runtime.Serialization.ISerializable> Implementuje rozhraní.

- <xref:System.SerializableAttribute> Má atribut použit.

> [!NOTE]
> Další informace týkající se vytvoření vzdáleně .NET Framework objektů naleznete v tématu věnovaném odvolání objektů, které se [provádí vzdáleně](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100)).

Typy uživatelského rozhraní WPF nejsou vzdáleně. Chcete-li tento problém vyřešit, WPF rozšiřuje model doplňku .NET Framework tak, aby bylo možné zobrazit uživatelské rozhraní WPF vytvořené pomocí doplňků v hostitelských aplikacích. Tuto podporu poskytuje WPF <xref:System.AddIn.Contract.INativeHandleContract> pomocí dvou typů: rozhraní a dvě statické metody implementované <xref:System.AddIn.Pipeline.FrameworkElementAdapters> třídou: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Na vysoké úrovni jsou tyto typy a metody použity následujícím způsobem:

1. WPF vyžaduje, aby uživatelská rozhraní poskytovaná doplňky byly třídy, které jsou odvozeny přímo nebo <xref:System.Windows.FrameworkElement>nepřímo z, například tvary, ovládací prvky, uživatelské ovládací prvky, panely rozložení a stránky.

2. Ať už kontrakt deklaruje, že uživatelské rozhraní bude předáno mezi doplňkem a hostitelskou aplikací, musí být deklarováno jako <xref:System.AddIn.Contract.INativeHandleContract> (not a <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> je vzdáleně reprezentací uživatelského rozhraní doplňku, které lze předat přes hranice izolace.

3. Před předáním z aplikační domény doplňku je objekt <xref:System.Windows.FrameworkElement> zabalen <xref:System.AddIn.Contract.INativeHandleContract> jako voláním metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.

4. Po předání do aplikační domény <xref:System.AddIn.Contract.INativeHandleContract> hostitelské aplikace musí být znovu zabalené <xref:System.Windows.FrameworkElement> jako voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.

Způsoby <xref:System.AddIn.Contract.INativeHandleContract>použití <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, a<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> jsou závislé na konkrétním scénáři. Následující části obsahují podrobné informace o jednotlivých programovacích modelech.

<a name="ReturnUIFromAddInContract"></a>

## <a name="add-in-returns-a-user-interface"></a>Doplněk vrátí uživatelské rozhraní.

Pro doplněk, který vrací uživatelské rozhraní pro hostitelskou aplikaci, jsou potřeba následující:

1. Je třeba vytvořit hostitelskou aplikaci, doplněk a kanál, jak je popsáno v dokumentaci .NET Framework [Doplňky a rozšiřitelnost](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) .

2. Kontrakt musí implementovat <xref:System.AddIn.Contract.IContract> a, aby vracel uživatelské rozhraní, kontrakt musí deklarovat metodu s návratovou hodnotou typu <xref:System.AddIn.Contract.INativeHandleContract>.

3. Uživatelské rozhraní, které je předáno mezi doplňkem a hostitelskou aplikací, se musí přímo nebo nepřímo <xref:System.Windows.FrameworkElement>odvozovat z.

4. Uživatelské rozhraní, které je vráceno doplňkem, musí být převedeno z <xref:System.Windows.FrameworkElement> typu <xref:System.AddIn.Contract.INativeHandleContract> na a před vyvoláním hranice izolace.

5. Navrácené uživatelské rozhraní musí být převedeno z <xref:System.AddIn.Contract.INativeHandleContract> typu na <xref:System.Windows.FrameworkElement> a po překročení hranice izolace.

6. Hostitelská aplikace zobrazí vrácenou <xref:System.Windows.FrameworkElement>aplikaci.

Příklad, který ukazuje, jak implementovat doplněk, který vrací uživatelské rozhraní, najdete v tématu [Vytvoření doplňku, který vrací uživatelské rozhraní](how-to-create-an-add-in-that-returns-a-ui.md).

<a name="AddInIsAUI"></a>

## <a name="add-in-is-a-user-interface"></a>Doplněk je uživatelské rozhraní.

Když je doplněk uživatelským rozhraním, vyžadují se následující:

1. Je třeba vytvořit hostitelskou aplikaci, doplněk a kanál, jak je popsáno v dokumentaci .NET Framework [Doplňky a rozšiřitelnost](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) .

2. Rozhraní kontraktu pro doplněk musí implementovat <xref:System.AddIn.Contract.INativeHandleContract>.

3. Doplněk, který je předán do hostitelské aplikace, musí přímo nebo nepřímo odvozovat z <xref:System.Windows.FrameworkElement>.

4. Doplněk musí být převeden z typu <xref:System.Windows.FrameworkElement> <xref:System.AddIn.Contract.INativeHandleContract> na a před převedením hranice izolace.

5. Doplněk musí být převeden z typu <xref:System.AddIn.Contract.INativeHandleContract> na a <xref:System.Windows.FrameworkElement> po překročení hranice izolace.

6. Hostitelská aplikace zobrazí vrácenou <xref:System.Windows.FrameworkElement>aplikaci.

Příklad, který ukazuje, jak implementovat doplněk, který je uživatelským rozhraním, najdete v tématu [Vytvoření doplňku, který je uživatelské rozhraní](how-to-create-an-add-in-that-is-a-ui.md).

<a name="ReturningMultipleUIsFromAnAddIn"></a>

## <a name="returning-multiple-uis-from-an-add-in"></a>Vrácení více uživatelská rozhraní z doplňku

Doplňky často poskytují více uživatelských rozhraní pro zobrazení hostitelských aplikací. Představte si například doplněk, který je uživatelské rozhraní, které také poskytuje informace o stavu pro hostitelskou aplikaci, a to také jako uživatelské rozhraní. Doplněk podobný tomuto může být implementován pomocí kombinace techniků z obou [doplňků vrátí uživatelské rozhraní](#ReturnUIFromAddInContract) a [doplněk je model uživatelského rozhraní](#AddInIsAUI) .

<a name="AddInsAndXBAPs"></a>

## <a name="add-ins-and-xaml-browser-applications"></a>Doplňky a aplikace prohlížeče XAML

V níže uvedených příkladech byla hostitelská aplikace nainstalována samostatnou aplikací. Ale [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] můžou taky hostovat doplňky, i když s následujícími dodatečnými požadavky na sestavení a implementaci:

- Manifest aplikace musí být nakonfigurován speciálně ke stažení kanálu (složky a sestavení) a sestavení doplňku v mezipaměti aplikace ClickOnce na klientském počítači ve stejné složce [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]jako. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]

- Kód pro zjišťování a načítání doplňků musí použít mezipaměť aplikace ClickOnce [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pro jako kanál a umístění doplňku. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]

- Je nutné načíst doplněk do speciálního kontextu zabezpečení, pokud doplněk odkazuje na volné soubory nacházející se v lokalitě původu; při hostování nástrojem [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]mohou doplňky odkazovat pouze na volné soubory, které se nacházejí v lokalitě hostitelské aplikace. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] původu.

Tyto úlohy jsou podrobně popsány v následujících pododdílech.

### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Konfigurace kanálu a doplňku pro nasazení ClickOnce

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]jsou staženy do a spouštěny z bezpečné složky v mezipaměti nasazení ClickOnce. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Aby mohl hostitel hostovat doplněk, musí se také stáhnout kanál a sestavení doplňku do složky Safe. Chcete-li to dosáhnout, je nutné nakonfigurovat manifest aplikace tak, aby zahrnoval sestavení kanálu i doplňku pro stažení. To je nejsnadnější [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], i když sestavení kanálu a doplňku musí být v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] kořenové složce projektu hostitele [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , aby bylo možné detekovat sestavení kanálu.

V důsledku toho je prvním krokem sestavení kanálu a sestavení [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doplňku v kořenu projektu nastavením výstupu sestavení pro každé sestavení kanálu a projektů sestavení doplňku. V následující tabulce jsou uvedeny výstupní cesty sestavení pro projekty sestavení kanálu a projekt sestavení doplňku, které jsou ve stejném řešení a kořenové složce jako hostitelský [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projekt.

Tabulka 1: Vytvoření výstupních cest pro sestavení kanálu, které jsou hostovány v XBAP

|Projekt sestavení kanálu|Výstupní cesta sestavení|
|-------------------------------|-----------------------|
|Kontrakt|`..\HostXBAP\Contracts\`|
|Zobrazení doplňku|`..\HostXBAP\AddInViews\`|
|Adaptér na straně doplňku|`..\HostXBAP\AddInSideAdapters\`|
|Adaptér na straně hostitele|`..\HostXBAP\HostSideAdapters\`|
|Doplněk|`..\HostXBAP\AddIns\WPFAddIn1`|

Dalším krokem je zadání sestavení kanálu a sestavení doplňku jako [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] souborů obsahu v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] nástroji pomocí následujícího postupu:

1. Zahrnutí sestavení kanálu a doplňku v projektu kliknutím pravým tlačítkem myši na jednotlivé složky kanálů v Průzkumník řešení a zvolením možnosti **zahrnout do projektu**.

2. Nastavení **Akce sestavení** každého sestavení kanálu a sestavení doplňku k **obsahu** z okna **vlastnosti** .

Posledním krokem je nakonfigurovat manifest aplikace tak, aby zahrnoval soubory sestavení kanálu a soubor sestavení doplňku pro stažení. Soubory by se měly nacházet ve složkách v kořenu složky v mezipaměti ClickOnce, kterou [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] aplikace zabírá. Konfiguraci můžete dosáhnout [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] pomocí následujícího postupu:

1. Klikněte pravým tlačítkem [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] na projekt, klikněte na **vlastnosti**, klikněte na **publikovat**a pak klikněte na tlačítko **soubory aplikace** .

2. V dialogovém okně **soubory aplikace** nastavte **stav publikování** každého kanálu a knihovny DLL doplňku, aby zahrnovaly **(auto)** , a nastavte **skupinu stažení** pro každý kanál a knihovnu DLL doplňku na **(povinné)** .

### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Použití kanálu a doplňku z základu aplikace

Pokud je kanál a doplněk nakonfigurován pro nasazení ClickOnce, jsou staženy do stejné složky mezipaměti ClickOnce jako [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Chcete-li použít kanál a doplněk z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , je nutné kód získat z základu aplikace. Různé typy a členové modelu doplňku .NET Framework pro použití kanálů a doplňků poskytují speciální podporu pro tento scénář. Za prvé je cesta identifikována <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> hodnotou výčtu. Tuto hodnotu použijete s přetíženími relevantních členů doplňku pro použití kanálů, které zahrnují následující:

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

### <a name="accessing-the-hosts-site-of-origin"></a>Přístup k webu původu hostitele

Aby bylo zajištěno, že doplněk může odkazovat na soubory z lokality původu, doplněk musí být načten s izolací zabezpečení, která je ekvivalentní s hostitelskou aplikací. Tato úroveň zabezpečení je identifikována <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> hodnotou výčtu a je předána <xref:System.AddIn.Hosting.AddInToken.Activate%2A> metodě, když je doplněk aktivován.

<a name="WPFAddInModelArchitecture"></a>

## <a name="wpf-add-in-architecture"></a>Architektura doplňku WPF

Na nejvyšší úrovni, jak jsme viděli, WPF umožňuje .NET Framework doplňky pro implementaci uživatelských rozhraní (které jsou odvozeny přímo nebo nepřímo <xref:System.Windows.FrameworkElement>z) <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> pomocí <xref:System.AddIn.Contract.INativeHandleContract>a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Výsledkem je, že hostitelská aplikace je vrácena <xref:System.Windows.FrameworkElement> , která je zobrazena z uživatelského rozhraní v hostitelské aplikaci.

V případě jednoduchých scénářů doplňků uživatelského rozhraní je to tolik podrobností, kolik vývojář vyžaduje. Pro složitější scénáře, zejména ty, které se pokoušejí využít další služby WPF, jako je například rozložení, prostředky a datové vazby, podrobnější znalosti o tom, jak WPF rozšiřuje model .NET Framework s podporou uživatelského rozhraní, je nutná k pochopení svých výhod. a omezení.

V podstatě nepředá WPF uživatelské rozhraní z doplňku do hostitelské aplikace; místo toho WPF předá popisovač okna Win32 pro uživatelské rozhraní pomocí interoperability WPF. V takovém případě, když je uživatelské rozhraní z doplňku předáno do hostitelské aplikace, dojde k následujícímu:

- Na straně doplňku WPF získá popisovač okna pro uživatelské rozhraní, které bude zobrazeno hostitelskou aplikací. Popisovač okna je zapouzdřen interní třídou WPF, která je odvozena z <xref:System.Windows.Interop.HwndSource> a implementuje. <xref:System.AddIn.Contract.INativeHandleContract> Instance této třídy je vrácena nástrojem <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> a je zařazena z aplikační domény doplňku do domény aplikace hostitelské aplikace.

- Na straně hostitele aplikace WPF znovu zabalí <xref:System.Windows.Interop.HwndSource> jako interní třídu WPF, která je odvozena z <xref:System.Windows.Interop.HwndHost> a spotřebovává <xref:System.AddIn.Contract.INativeHandleContract>. Instance této třídy je vrácena <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> do hostitelské aplikace.

<xref:System.Windows.Interop.HwndHost>existuje pro zobrazení uživatelských rozhraní identifikovaných popisovači okna, od uživatelských rozhraní WPF. Další informace najdete v tématu [spolupráce WPF a Win32](../advanced/wpf-and-win32-interoperation.md).

V souhrnech <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> existují, pokud chcete, aby popisovač okna pro uživatelské rozhraní WPF byl předán z doplňku do hostitelské aplikace <xref:System.Windows.Interop.HwndHost> , kde je zapouzdřen a zobrazen v uživatelském rozhraní hostitelské aplikace.

> [!NOTE]
> Vzhledem k tomu <xref:System.Windows.Interop.HwndHost>, že hostitelská aplikace získá, hostitelská aplikace nemůže převést objekt, který <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> je vrácen na typ, který je implementován jako doplněk (například a <xref:System.Windows.Controls.UserControl>).

Podle jeho povahy má <xref:System.Windows.Interop.HwndHost> určitá omezení, která mají vliv na to, jak je hostitelská aplikace může používat. WPF ale rozšiřuje <xref:System.Windows.Interop.HwndHost> několik možností pro scénáře doplňku. Tyto výhody a omezení jsou popsány níže.

<a name="WPFAddInModelBenefits"></a>

## <a name="wpf-add-in-benefits"></a>Výhody doplňku WPF

Vzhledem k tomu, že jsou uživatelská rozhraní doplňku WPF zobrazena z hostitelských aplikací pomocí interní třídy, <xref:System.Windows.Interop.HwndHost>která je odvozena z, jsou tato uživatelská rozhraní omezená <xref:System.Windows.Interop.HwndHost> funkcemi nástroje s ohledem na služby uživatelského rozhraní WPF, jako je například rozložení, vykreslování, datové vazby, styly, šablony a prostředky. WPF ale rozšiřuje svou vnitřní <xref:System.Windows.Interop.HwndHost> podtřídu o další možnosti, které zahrnují následující:

- Procházení mezi uživatelským rozhraním hostitelské aplikace a uživatelským rozhraním doplňku Všimněte si, že "doplněk je programovací model uživatelského rozhraní, který vyžaduje přepsání <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> adaptéru doplňky, aby bylo možné povolit tabulátory, zda je doplněk plně důvěryhodný nebo částečně důvěryhodný.

- Respektují se požadavky na přístupnost pro uživatelská rozhraní doplňku, která se zobrazují z uživatelských rozhraní aplikace hostitele.

- Umožnění bezpečného spouštění aplikací WPF ve více scénářích domény aplikace.

- Zabránění neoprávněnému přístupu k oknu uživatelského rozhraní doplňku se zpracovává, když se doplňky spustí s izolací zabezpečení (tj. izolovaný prostor zabezpečení s částečným vztahem důvěryhodnosti). Volání <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> zajišťuje toto zabezpečení:

  - Pro doplněk vrátí programovací model uživatelského rozhraní, jediným způsobem, jak předat popisovač okna pro uživatelské rozhraní doplňku v rámci hranice izolace, je zavolat <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.

  - Pro doplněk je programovací model uživatelského rozhraní, přepsání <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> na adaptéru doplňků a volání <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (jak je znázorněno v předchozích příkladech) je povinné, protože volá `QueryContract` implementaci adaptéru doplňku na straně. adaptér na straně hostitele.

- Zajištění vícenásobné ochrany spuštění aplikační domény. Z důvodu omezení u domén aplikace způsobí neošetřené výjimky, které jsou vyvolány v doménách aplikace doplňku, příčinou selhání celé aplikace, i když hranice izolace existuje. Nicméně WPF a Model doplňku .NET Framework poskytují jednoduchý způsob, jak tento problém obejít a zlepšit stabilitu aplikace. Doplněk WPF, který zobrazuje uživatelské rozhraní vytvoří <xref:System.Windows.Threading.Dispatcher> pro vlákno, na kterém běží doména aplikace, pokud je hostitelská aplikace WPF. Můžete detekovat všechny neošetřené výjimky, ke kterým dojde v doméně aplikace, pomocí zpracování <xref:System.Windows.Threading.Dispatcher.UnhandledException> události doplňku <xref:System.Windows.Threading.Dispatcher>WPF. <xref:System.Windows.Threading.Dispatcher> Z vlastnostimůžetezískat.<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>

<a name="WPFAddInModelLimitations"></a>

## <a name="wpf-add-in-limitations"></a>Omezení doplňku WPF

Kromě výhod, které WPF přidávají do výchozího chování <xref:System.Windows.Interop.HwndSource>dodaného <xref:System.Windows.Interop.HwndHost>obslužnými rutinami, a, existují také omezení pro uživatelská rozhraní doplňku, která se zobrazují z hostitelských aplikací:

- Uživatelská rozhraní doplňku zobrazená z hostitelské aplikace nerespektují chování oříznutí hostitelské aplikace.

- Pojem vzdušného *prostoru* ve scénářích interoperability platí i pro doplňky (viz [Přehled technologických oblastí](../advanced/technology-regions-overview.md)).

- Služby uživatelského rozhraní hostitelské aplikace, jako je dědění prostředků, vázání dat a příkazy, nejsou automaticky k dispozici pro uživatelská rozhraní doplňku. Chcete-li poskytnout tyto služby doplňku, je nutné kanál aktualizovat.

- Uživatelské rozhraní doplňku nelze otočit, škálovat, zkosit nebo jinak ovlivněné transformací (viz [Přehled transformací](../graphics-multimedia/transforms-overview.md)).

- Obsah uvnitř uživatelských rozhraní doplňku, která jsou vykreslena operacemi vykreslování z <xref:System.Drawing> oboru názvů, mohou zahrnovat prolnutí alfa. V uživatelském rozhraní doplňku i v uživatelském rozhraní hostitelské aplikace, které obsahuje, musí být 100% neprůhledné; Jinými slovy, `Opacity` vlastnost u obou musí být nastavená na hodnotu 1.

- Pokud je `true`vlastnost okna v hostitelské aplikaci, která obsahuje uživatelské rozhraní doplňku, nastavena na, doplněk je neviditelná. <xref:System.Windows.Window.AllowsTransparency%2A> To platí i v případě, že uživatelské rozhraní doplňku je 100% neprůhledné (to `Opacity` znamená, že vlastnost má hodnotu 1).

- Uživatelské rozhraní doplňku se musí nacházet nad ostatními prvky WPF v rámci stejného okna nejvyšší úrovně.

- Žádná část uživatelského rozhraní doplňku nemůže být vykreslena pomocí <xref:System.Windows.Media.VisualBrush>. Místo toho doplněk může pořídit snímek vygenerovaného uživatelského rozhraní, aby vytvořil rastrový obrázek, který lze předat aplikaci hostitele pomocí metod definovaných v kontraktu.

- Soubory médií nelze přehrát <xref:System.Windows.Controls.MediaElement> v uživatelském rozhraní doplňku.

- Události myši generované pro uživatelské rozhraní doplňku nejsou přijaty ani aktivovány hostitelskou aplikací a `IsMouseOver` vlastnost uživatelského rozhraní aplikace hostitele má `false`hodnotu.

- Když se fokus zaměřuje mezi ovládacími prvky v uživatelském rozhraní doplňku, `GotFocus` události `LostFocus` a nejsou ani od hostitelské aplikace přijaty ani vyvolány.

- Část hostitelské aplikace, která obsahuje uživatelské rozhraní doplňku, se při tisku zobrazí bíle.

- Všechny odchody (viz <xref:System.Windows.Threading.Dispatcher>), které byly vytvořeny pomocí uživatelského rozhraní doplňku, musí být před uvolněním doplňku vlastníka vypnuty ručně, pokud hostitelská aplikace pokračuje v provádění. Kontrakt může implementovat metody, které umožní, aby hostitelská aplikace vykázala doplněk před uvolněním doplňku, a tím umožňuje uživatelskému doplňku ukončit své odeslané součásti.

- Pokud je <xref:System.Windows.Controls.InkCanvas> uživatelské rozhraní doplňku nebo <xref:System.Windows.Controls.InkCanvas>obsahuje, nelze zrušit načtení doplňku.

<a name="PerformanceOptimization"></a>

## <a name="performance-optimization"></a>Optimalizace výkonu

Ve výchozím nastavení platí, že při použití více domén aplikace jsou všechna .NET Framework sestavení požadovaná každou aplikací načtena do domény této aplikace. V důsledku toho může mít vliv na výkon čas potřebný k vytvoření nových aplikačních domén a spouštění aplikací v nich. .NET Framework však poskytuje způsob, jak můžete zkrátit dobu spouštění tím, že dáte pokyn ke sdílení sestavení napříč doménami aplikace v případě, že jsou již načteny. To provedete pomocí <xref:System.LoaderOptimizationAttribute> atributu, který musí být použit pro metodu vstupního bodu (`Main`). V takovém případě je nutné použít pouze kód k implementaci definice vaší aplikace (viz [Přehled správy aplikací](application-management-overview.md)).

## <a name="see-also"></a>Viz také:

- <xref:System.LoaderOptimizationAttribute>
- [Doplňky a rozšíření](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Aplikační domény](../../app-domains/application-domains.md)
- [Přehled vzdálené komunikace .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [Vytváření objektů – vzdáleně](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [Témata s postupy](how-to-topics.md)
