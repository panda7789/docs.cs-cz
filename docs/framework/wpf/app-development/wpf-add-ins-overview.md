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
ms.openlocfilehash: 2e5d133a4744124723c0373e3d5974b505936190
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402098"
---
# <a name="wpf-add-ins-overview"></a>Přehled doplňků WPF
<a name="Introduction"></a> [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Obsahuje doplněk model, pomocí kterých mohou vývojáři vytvářet aplikace, které podporují rozšiřitelnosti doplňku. Tento model doplňku umožňuje vytvářet doplňky, které integrovat a rozšířit funkce aplikace. V některých scénářích aplikací také potřebovat zobrazit [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] , které jsou poskytovány doplňky. Toto téma ukazuje, jak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] navyšuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu doplňku povolit tyto scénáře, architektura jeho, jeho výhody a omezení.  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>Požadavky  
 Znalost [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku je model požadován. Další informace najdete v tématu [doplňků a rozšíření](../../../../docs/framework/add-ins/index.md).  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>Přehled doplňků  
 Pokud se chcete vyhnout složitosti rekompilace aplikace a opětovné nasazení k začlenění nové funkce, aplikace implementovat mechanismy rozšiřitelnosti, které umožňují vývojářům (první strany a třetích stran) k vytvoření dalších aplikací, které Integrace s nimi. Pomocí doplňků (označované také jako "doplňky" a "moduly plug-in") je nejběžnějším způsobem podporují tento typ rozšíření. Mezi příklady z reálného světa aplikací, které zpřístupňují rozšiřitelnosti s doplňky patří:  
  
-   Doplňky aplikace Internet Explorer.  
  
-   Windows Media Player moduly plug-in.  
  
-   Visual Studio doplňky.  
  
 Například model doplňku Windows Media Player umožňuje vývojářům třetích stran k implementaci "moduly plug-in", které rozšiřují Windows Media Player v celou řadu způsobů, včetně vytváření dekodérů a kodérů pro formáty multimédií, které nativně nepodporují ve Windows Media Player (například DVD, MP3), zvukové efekty a skinů v šablonách. Každý model doplňku je určený pro funkci, která je jedinečné pro aplikace, i když existuje několik entit a chování, které jsou společné pro všechny modely doplňku.  
  
 Jsou tři hlavní entity typické rozšiřitelnosti doplňku řešení *kontrakty*, *doplňky*, a *hostovat aplikace*. Kontrakty definovat, jak doplňky integrace s aplikacemi hostitele dvěma způsoby:  
  
-   Doplňky integrace s funkcí, které je implementované Hostování aplikací.  
  
-   Hostování aplikací zpřístupnění funkcí pro doplňky integrovat.  
  
 Doplňky se použije, hostování aplikací nutné k jejich vyhledání a načtení za běhu. Aplikace, které podporují doplňky v důsledku toho vyplývají následující dodatečné povinnosti:  
  
-   **Zjišťování**: hledání doplňků, které se řídí kontrakty nepodporuje hostování aplikací.  
  
-   **Aktivace**: načítání, spuštění a navázání komunikace s doplňky.  
  
-   **Izolace**: vytvoření hranice izolace ochránit aplikace před potenciální problémy zabezpečení a provádění s doplňky pomocí domén aplikace nebo procesy.  
  
-   **Komunikace**: povolení doplňky a hostovat aplikace komunikovat mezi sebou přes hranice izolace pomocí volání metody a předávání dat.  
  
-   **Správa životního cyklu**: načítání a uvolňování domény aplikace a procesy vyčistit a předvídatelným způsobem (viz [aplikačních doménách](../../../../docs/framework/app-domains/application-domains.md)).  
  
-   **Správa verzí**: zajištění, že hostovat aplikace a doplňky stále komunikovat při vytváření nové verze buď.  
  
 Nakonec vývoj robustní model doplňku je netriviální podniku. Z tohoto důvodu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytuje infrastrukturu pro vytváření modelů po doplňku.  
  
> [!NOTE]
>  Podrobnější informace o doplňcích, najdete v článku [doplňků a rozšíření](../../../../docs/framework/add-ins/index.md).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>Přehled modelu doplňku rozhraní .NET framework  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] – Model doplňku, součástí <xref:System.AddIn> obor názvů obsahuje sadu typů, které jsou navržené pro zjednodušení vývoje rozšiřitelnosti doplňku. Základní jednotku [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] v modelu doplňku je *kontraktu*, která definuje způsob, jakým hostitelskou aplikaci a doplněk komunikovat mezi sebou. Kontrakt je přístupný pro hostitelskou aplikaci používat hostiteli specifické pro aplikaci *zobrazení* kontraktu. Podobně přidat v konkrétní *zobrazení* kontraktu je přístupný add-in. *Adaptér* slouží k povolení hostitele aplikace a doplněk ke komunikaci mezi jejich příslušných zobrazeních kontraktu. Kontrakty, zobrazení a adaptéry jsou označovány jako segmentů a představuje sadu souvisejících segmentů *kanálu*. Kanály jsou základem, na kterém [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplněk model podporuje zjišťování aktivace, izolace zabezpečení, izolaci spuštění (pomocí domény aplikace a procesy), komunikace, Správa životního cyklu a správy verzí.  
  
 Součet tato podpora umožňuje vývojářům vytvářet doplňky, které se integrují s funkcemi hostitelskou aplikaci. Některé scénáře však vyžadují hostování aplikací zobrazíte [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] poskytované doplňky. Protože každý prezentace technologie v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] má svůj vlastní model pro implementaci [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplněk model nepodporuje žádné konkrétní prezentace technologie. Místo toho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu doplňku s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] podporu pro doplňky.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>Doplňků WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ve spojení s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku v modelu, můžete k vyřešení širokou škálu scénářů, které vyžadují hostování aplikací zobrazíte [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] z doplňků. Konkrétně se tyto scénáře jsou vyřešeny [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pomocí následujících dvou programovacích modelů:  
  
1.  **Doplněk vrací uživatelské rozhraní**. Vrací doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] hostitelské aplikace prostřednictvím volání metody, jak je definováno ve smlouvě. Tento scénář se používá v následujících případech:  
  
    -   Vzhled [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který je vrácen doplňku je závislá na obou data nebo podmínek, které existují pouze v době běhu, jako například dynamicky generované sestavy.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Služby poskytované doplněk se liší od [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] hostitele aplikací, které můžete použít doplněk.  
  
    -   Doplněk primárně provádí služba pro hostitelskou aplikaci a hlásí stav do hostitelské aplikace s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
2.  **Doplněk je uživatelským rozhraním**. Doplněk je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], jak je definováno ve smlouvě. Tento scénář se používá v následujících případech:  
  
    -   Doplněk neposkytuje jinými službami než zobrazení, jako je například reklamu.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Pro služby poskytované doplňku je společné pro všechny hostitelské aplikace, které můžete použít tento doplněk, jako je například Kalkulačka nebo výběr barvy.  
  
 Tyto scénáře vyžadují, aby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] lze předat objekty mezi hostitele aplikací a domén aplikace doplňku. Protože [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplněk modelu spoléhá na vzdálené komunikace pro komunikaci mezi doménami aplikace objekty, které jsou předávány mezi nimi musí být podpory vzdáleného přístupu.  
  
 Objekt lze použít vzdáleně je instance třídy, která provádí jeden nebo více z následujících akcí:  
  
-   Je odvozen od <xref:System.MarshalByRefObject> třídy.  
  
-   Implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
-   Má <xref:System.SerializableAttribute> atribut.  
  
> [!NOTE]
>  Další informace týkající se vytváření vzdáleně nastavitelné [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty, najdete [provádění lze použít vzdáleně objekty](https://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Typy nejsou podpory vzdáleného přístupu. K vyřešení problému, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu doplňku umožňující [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vytvořil doplňky zobrazený z hostitele aplikací. Tato podpora poskytuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dva typy: <xref:System.AddIn.Contract.INativeHandleContract> rozhraní a dvě statické metody implementované <xref:System.AddIn.Pipeline.FrameworkElementAdapters> třídy: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Na vysoké úrovni se používají tyto typy a metody následujícím způsobem:  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vyžaduje, aby [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] poskytované doplňky jsou třídy, které jsou přímo nebo nepřímo odvozeny z <xref:System.Windows.FrameworkElement>, jako jsou například obrazce, ovládací prvky, uživatelské ovládací prvky, panely rozložení a stránky.  
  
2.  Bez ohledu na to kontrakt deklaruje, že uživatelské rozhraní se předají mezi doplněk a hostitelskou aplikací, musí být deklarována jako <xref:System.AddIn.Contract.INativeHandleContract> (ne <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> je vzdáleně nastavitelné reprezentace doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , které mohou být předány přes hranice izolace.  
  
3.  Před předáním od doplňku na aplikační domény <xref:System.Windows.FrameworkElement> je zabalený jako <xref:System.AddIn.Contract.INativeHandleContract> voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Po předávaný do hostitelské aplikace domény aplikace, <xref:System.AddIn.Contract.INativeHandleContract> musí být vytvořen nový balíček <xref:System.Windows.FrameworkElement> voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Jak <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> použijí, závisí na konkrétní scénář. Následující části obsahují podrobnosti o jednotlivých programovací model.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>Doplněk vrací uživatelské rozhraní  
 Pro doplněk se vraťte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro hostitelskou aplikaci, vyžadují se následující věci:  
  
1.  Hostitelskou aplikaci a kanál musí vytvořit, jak je popsáno [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [doplňků a rozšíření](../../../../docs/framework/add-ins/index.md) dokumentaci.  
  
2.  Musí implementovat kontrakt <xref:System.AddIn.Contract.IContract> a vrátit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], kontrakt musí deklarovat metody s návratovou hodnotou typu <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , Který je předán mezi doplněk a hostitelem aplikace musí přímo nebo nepřímo odvozovat z: <xref:System.Windows.FrameworkElement>.  
  
4.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , Který je vrácen doplněk musejí být převedeny z <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> před překročení hranice izolace.  
  
5.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , Která je vrácena, musejí být převedeny z <xref:System.AddIn.Contract.INativeHandleContract> k <xref:System.Windows.FrameworkElement> po překročení hranice izolace.  
  
6.  Hostitelská aplikace zobrazí vráceného <xref:System.Windows.FrameworkElement>.  
  
 Příklad, který ukazuje, jak implementovat doplněk, který vrací [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], naleznete v tématu [vytvořit doplňku, který vrací uživatelské rozhraní](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>Doplněk je uživatelské rozhraní  
 Když je doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], vyžadují se následující věci:  
  
1.  Hostitelskou aplikaci a kanál musí vytvořit, jak je popsáno [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [doplňků a rozšíření](../../../../docs/framework/add-ins/index.md) dokumentaci.  
  
2.  Musí implementovat rozhraní kontraktu pro doplněk <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Doplněk, který je předán do hostitelské aplikace musí přímo nebo nepřímo odvozovat z: <xref:System.Windows.FrameworkElement>.  
  
4.  Doplněk musejí být převedeny z <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> před překročení hranice izolace.  
  
5.  Doplněk musejí být převedeny z <xref:System.AddIn.Contract.INativeHandleContract> k <xref:System.Windows.FrameworkElement> po překročení hranice izolace.  
  
6.  Hostitelská aplikace zobrazí vráceného <xref:System.Windows.FrameworkElement>.  
  
 Příklad, který ukazuje, jak implementovat doplňku, který je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], naleznete v tématu [vytvoření uživatelského rozhraní doplňku, který je](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Vrácení více uživatelských rozhraní z doplňku  
 Doplňky často poskytují více [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] pro hostování aplikací zobrazíte. Představte si třeba doplňku, který je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který také obsahuje informace o stavu do hostitelské aplikace také jako [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Doplněk tímto způsobem můžete implementovat pomocí kombinace postupů z obou [vrátí Add-In uživatelské rozhraní](#ReturnUIFromAddInContract) a [doplňku je uživatelské rozhraní](#AddInIsAUI) modely.  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>Doplňky a aplikace prohlížeče XAML  
 V příkladech zatím hostitelská aplikace byla nainstalovaná samostatná aplikace. Ale [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] můžou hostovat taky doplňků, spolu s následující další sestavení a provádění požadavků:  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Manifestu aplikace musí být nakonfigurován speciálně pro stahování kanálu (složky a sestavení) a přidejte sestavení do [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] mezipaměti aplikace v klientském počítači ve stejné složce jako [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Kód zjišťovat a načíst doplňků musí použít [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] mezipaměti aplikace pro [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jako umístění a kanálu doplňku.  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Musí načtení doplňku do kontextu zabezpečení speciální Pokud doplněk odkazuje volné soubory, které se nachází v umístění původních; když jsou hostované ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], doplňky mohou odkazovat pouze na volné soubory, které jsou umístěné na serveru hostitele aplikace původu.  
  
 Tyto úlohy jsou popsány podrobně v následujících oddílech.  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Konfigurace kanálu a Add-In pro nasazení ClickOnce  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] jsou stahovat a spouštět ze složky v nouzovém [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] mezipaměti nasazení. Aby se [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] k hostování doplňku, je nutné stáhnout sestavení kanálu a doplněk ke složce bezpečné. K dosažení tohoto cíle, musíte nakonfigurovat manifest aplikace zahrnout kanálu a sestavení doplňku pro stahování. To se provádí nejsnadněji v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], i když sestavení kanálu a doplněk musí být na hostiteli [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kořenové složce projektu mohl [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] ke zjištění sestavení kanálu.  
  
 V důsledku toho prvním krokem je vytvoření kanálu a sestavení doplňku do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kořenové projektu tak, že nastavíte sestavení a přidat do projektů sestavení výstupu sestavení každý kanál. V následující tabulce jsou uvedeny výstupní cesta sestavení pro projekty kanálu sestavení a sestavení doplňku v projektu, které jsou ve stejném řešení a kořenové složky jako hostitel [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu.  
  
 Tabulka 1: Vytvořit výstupní cesty pro kanál sestavení, které jsou hostované XBAP  
  
|Projekt sestavení kanálu|Výstupní cesta sestavení|  
|-------------------------------|-----------------------|  
|Kontrakt|`..\HostXBAP\Contracts\`|  
|Zobrazení doplňku|`..\HostXBAP\AddInViews\`|  
|Přidat v-adaptér na straně|`..\HostXBAP\AddInSideAdapters\`|  
|Adaptér na straně hostitele|`..\HostXBAP\HostSideAdapters\`|  
|Add-In|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 Dalším krokem je zadání kanálu sestavení a sestavení doplňku jako [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] obsah souborů v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] následujícím způsobem:  
  
1.  Třeba sestavení a kanálu doplňku v projektu tak, že pravým tlačítkem myši na každý kanál složku v Průzkumníku řešení a zvolením **zahrnout do projektu**.  
  
2.  Nastavení **akce sestavení** jednotlivých kanálu sestavení a sestavení doplňku do **obsahu** z **vlastnosti** okna.  
  
 Posledním krokem je konfigurace manifestu aplikace do kanálu soubory sestavení a sestavení doplňku v souboru ke stažení. Soubory musíte umístit do složky v kořenové složce v [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] ukládat do mezipaměti, který [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] aplikace zabírá. Konfigurace můžete dosáhnout v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] následujícím způsobem:  
  
1.  Klikněte pravým tlačítkem na [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu, klikněte na tlačítko **vlastnosti**, klikněte na tlačítko **publikovat**a potom klikněte na tlačítko **soubory aplikace** tlačítko.  
  
2.  V **soubory aplikace** dialogové okno, nastavte **stav publikování** jednotlivých kanálů a knihovny DLL doplňku **Include (Auto)** a nastavte **skupina pro stažení** pro každý kanál a DLL – doplněk pro **(povinné)**.  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Použití kanálu a doplněk z základ cesty aplikace  
 Když na kanálu a jsou nakonfigurované pro [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nasazení, se stáhnou do stejné [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] složku mezipaměti, jako [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Použití kanálu a doplněk z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kódu nutné získat aplikace základní. Různé typy a členy [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model doplňku pomocí kanálů a doplňky poskytují zvláštní podporu pro tento scénář. Za prvé, je identifikován cestu <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> hodnota výčtu. Tuto hodnotu použijete s přetížení členů relevantní – doplněk pro práci s kanály, které zahrnují následující:  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Přístup k serveru hostitele původu  
 Aby bylo zajištěno, že doplněk lze odkazují na soubory webu původu, doplněk musí být načten izolace zabezpečení, který je ekvivalentní k hostitele aplikace. Tato úroveň zabezpečení je identifikován <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> hodnota výčtu a předat <xref:System.AddIn.Hosting.AddInToken.Activate%2A> metodu, když se aktivuje doplněk.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>Architektura doplňků WPF  
 Na nejvyšší úrovni jak jsme viděli, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňků k implementaci [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] (který přímo nebo nepřímo odvodit z <xref:System.Windows.FrameworkElement>) pomocí <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Výsledkem je, že se hostitelská aplikace vrátí <xref:System.Windows.FrameworkElement> , která se zobrazí z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v hostitelské aplikaci.  
  
 Pro jednoduché [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] doplněk scénáře, toto je co nejvíce podrobností vývojář potřebuje. Pro složitější scénáře, zvláště ta, která pokusí využívat další [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] služby, například rozložení, prostředky a datové vazby, podrobnější znalosti o tom, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu doplňku s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Podpora je potřeba pochopit jeho výhody a omezení.  
  
 V podstatě [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] neprojde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z doplňku pro hostitelskou aplikaci; místo toho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] předává popisovač okna Win32 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vzájemná funkční spolupráce. Jako takové, když [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z doplňku je předán do hostitelské aplikace, dojde k následujícímu:  
  
-   Na straně doplňku [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] získá popisovač okna pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který se zobrazí hostitelskou aplikací. Popisovač okna jsou zapouzdřena objektem interní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] třídu odvozenou od <xref:System.Windows.Interop.HwndSource> a implementuje <xref:System.AddIn.Contract.INativeHandleContract>. Instance této třídy je vrácený <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> a je zařazeno od doplňku na aplikační domény do domény aplikace hostitelskou aplikaci.  
  
-   Na straně hostitele aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sbalí <xref:System.Windows.Interop.HwndSource> jako interní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] třídu odvozenou od <xref:System.Windows.Interop.HwndHost> a využívá <xref:System.AddIn.Contract.INativeHandleContract>. Instance této třídy je vrácený <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> hostitelské aplikace.  
  
 <xref:System.Windows.Interop.HwndHost> existuje zobrazíte [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], identifikovaný popisovače okna z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Další informace najdete v tématu [WPF a systému Win32 vzájemná spolupráce grafického subsystému](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
 Stručně řečeno <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> umožňují popisovač okna pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] předat z doplňku pro hostitelskou aplikaci, ve kterém jsou zapouzdřena objektem <xref:System.Windows.Interop.HwndHost> a zobrazí hostitele aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  Protože hostitelská aplikace získá <xref:System.Windows.Interop.HwndHost>, hostitelské aplikace nelze převést na objekt, který je vrácený <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> typu ho je implementováno jako doplněk (například <xref:System.Windows.Controls.UserControl>).  
  
 Svou povahou <xref:System.Windows.Interop.HwndHost> má určitá omezení, které ovlivňují, jak hostovat aplikace je můžete využít. Ale [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje <xref:System.Windows.Interop.HwndHost> s několika možnostmi pro doplněk scénáře. Tyto výhody a omezení jsou popsané níže.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>WPF – doplněk výhody  
 Protože [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] doplněk [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] zobrazují z hostitele aplikací pomocí vnitřní třída, která je odvozena z <xref:System.Windows.Interop.HwndHost>, které [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] jsou omezeny funkce <xref:System.Windows.Interop.HwndHost> s ohledem na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] služeb, jako je rozložení, vykreslování, datových vazeb, styly, šablony a prostředky. Ale [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] posiluje interní <xref:System.Windows.Interop.HwndHost> podtřídy doplněná o funkce, které zahrnují následující:  
  
-   Přecházení mezi hostitelskou aplikaci pomocí tabulátoru [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Všimněte si, že "je doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programovací model vyžaduje adaptér přidat v na straně přepsat <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> povolit procházení tabulátorem, zda doplněk je plně důvěryhodné nebo částečně důvěryhodné.  
  
-   Aby byla dodržena požadavky na usnadnění přístupu pro doplněk [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] , který se zobrazí z aplikace hostitel [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
-   Povolení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, které poběží bezpečně ve scénářích s více domény aplikace.  
  
-   Neplatný přístup k doplňku brání [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zpracovává okno při spuštění doplňků izolace zabezpečení (to znamená, sandboxu částečným vztahem důvěryhodnosti zabezpečení). Volání <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> zajišťuje toto zabezpečení:  
  
    -   Pro "add-in vrátí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programovací model, jediný způsob, jak předat popisovač okna pro doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] napříč izolaci hranice je volat <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   Pro "doplněk je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programovací model, přepisování <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> přidat v vedle adaptéru a volání <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (jak je znázorněno v předchozích ukázkách) je nutné použít, jako je volání adaptér přidat v na straně `QueryContract` implementace z adaptér na straně hostitele.  
  
-   Poskytování více ochrana provádění domény aplikace. Vzhledem k omezením s aplikačními doménami způsobit neošetřené výjimky, které jsou vyvolány v doplňku v aplikačních doménách celé aplikace při selhání, i když existuje oddělovací hranice. Ale [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] – model doplňku poskytují jednoduchý způsob, jak tento problém vyřešit a zlepšit stabilita aplikace. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] doplněk, který se zobrazí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vytvoří <xref:System.Windows.Threading.Dispatcher> pro vlákno, na které domény aplikace poběží, pokud je hostitelská aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace. Můžete zjistit všechny neošetřené výjimky, ke kterým dochází v doméně aplikace pomocí manipulace <xref:System.Windows.Threading.Dispatcher.UnhandledException> událost [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] doplňku <xref:System.Windows.Threading.Dispatcher>. Můžete získat <xref:System.Windows.Threading.Dispatcher> z <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> vlastnost.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>WPF – doplněk omezení  
 Nad rámec výhody, které [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] přidá do výchozí chování poskytnutých <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>a popisovače oken, existují také omezení pro doplněk [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] , který se zobrazí z hostitele aplikací:  
  
-   Doplněk [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] zobrazí z hostitele aplikace neodpovídají chování výstřižek hostitelskou aplikaci.  
  
-   Konceptu *vzdušného prostoru* interoperabilitou scénáře platí také pro doplňky (viz [přehled technologických oblastí](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)).  
  
-   Hostitelská aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] služby, jako je dědičnost prostředků, datové vazby a příkazů, nejsou automaticky dostupné pro doplněk [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. K poskytování těchto služeb add-in, budete muset aktualizovat kanálu.  
  
-   Doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nemůže být otočen, škálovat, zkosený nebo jinak ovlivněná pomocí transformace (viz [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)).  
  
-   Obsah uvnitř doplněk [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] , který je vykreslen metodou kreslicí operace z <xref:System.Drawing> oboru názvů může zahrnovat alfa míchání. Však obě doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a hostitelskou aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který obsahuje musí být 100 % neprůhledný; jinými slovy, `Opacity` vlastnost u obou musí být nastavena na hodnotu 1.  
  
-   Pokud <xref:System.Windows.Window.AllowsTransparency%2A> vlastnost okna v hostiteli aplikace, která obsahuje doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je nastavena na `true`, doplněk je neviditelné. To platí i v případě, doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je neprůhledný 100 % (to znamená `Opacity` vlastnost má hodnotu 1).  
  
-   Doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musí být uvedena na jiné [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementy ve stejném okně nejvyšší úrovně.  
  
-   Žádná část doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] může být vykreslen pomocí <xref:System.Windows.Media.VisualBrush>. Místo toho doplněk může pořídit snímek generované [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vytvořit rastrový obrázek, který lze předat do hostitelské aplikace pomocí metody definované ve smlouvě.  
  
-   Multimediální soubory nelze přehrát z <xref:System.Windows.Controls.MediaElement> v doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Myš události vygenerované pro doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nejsou přijata ani vyvolané hostitelskou aplikaci a `IsMouseOver` vlastnost pro hostitelskou aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] má hodnotu `false`.  
  
-   Když se pozornost zaměří mezi ovládacími prvky v doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], `GotFocus` a `LostFocus` události nejsou přijata ani vyvolané hostitelskou aplikaci.  
  
-   Část aplikace hostitele, který obsahuje doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se zobrazí bílé po vytištění.  
  
-   Všechny dispečerů (naleznete v tématu <xref:System.Windows.Threading.Dispatcher>) vytvořené pomocí doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musí být vypnut ručně před doplňku vlastníka je uvolněna, pokud hostitelská aplikace pokračuje v provádění kódu. Smlouvy můžete implementovat metody, které umožňují hostitelskou aplikaci na signál doplňku před doplňku je uvolněna, což doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vypnout jeho dispečerů.  
  
-   Pokud doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je <xref:System.Windows.Controls.InkCanvas> nebo obsahuje <xref:System.Windows.Controls.InkCanvas>, není možné uvolnit doplňku.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Optimalizace výkonu  
 Ve výchozím nastavení, pokud se používá více domén aplikace různé [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sestavení vyžadované každé aplikace jsou všechny načtené do domény vaší aplikace. Čas potřebný k vytvoření nové domény aplikace a spouštění aplikací v nich v důsledku toho může ovlivnit výkon. Ale [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytuje způsob, jak můžete snížit dobu spuštění tím, že aplikace pro sdílení sestavení napříč doménami aplikace, pokud jsou už načteny. Můžete to provést pomocí <xref:System.LoaderOptimizationAttribute> atribut, který je nutné použít na metodu vstupního bodu (`Main`). V takovém případě je nutné použít pouze kód pro implementaci definice aplikace (viz [přehled správy aplikací](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.LoaderOptimizationAttribute>  
 [Doplňky a rozšíření](../../../../docs/framework/add-ins/index.md)  
 [Aplikační domény](../../../../docs/framework/app-domains/application-domains.md)  
 [Vzdálené komunikace .NET framework – přehled](https://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [Vytváření objektů lze používat vzdáleně](https://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)  
 [Témata s postupy](../../../../docs/framework/wpf/app-development/how-to-topics.md)
