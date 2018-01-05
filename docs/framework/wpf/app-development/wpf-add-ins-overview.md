---
title: "Přehled doplňků WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76a836e2699617803b78f76f90b27452bd0cdd0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-add-ins-overview"></a>Přehled doplňků WPF
<a name="Introduction"></a>[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zahrnuje přidat model, vývojáři mohou použít k vytvoření aplikace, které podporují doplňku rozšíření. Tento model doplňku umožňuje vytváření doplňků, které integrovat a rozšířit funkce aplikace. V některých scénářích aplikací také potřebovat zobrazit [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] jsou poskytovány doplňků. Toto téma ukazuje, jak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model doplňku povolit tyto scénáře, architektura hlouběji, její výhody a její omezení.  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>Požadavky  
 Znalost [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku je třeba použít model. Další informace najdete v tématu [doplňky a rozšíření](../../../../docs/framework/add-ins/index.md).  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>Přehled doplňky  
 Aby se zabránilo složitosti rekompilace aplikace a opětovné nasazení k začlenění nové funkce, aplikace implementaci rozšíření mechanismy, které umožňují vývojářům (první strany a třetích stran) pro vytvoření dalších aplikací, který integrate s nimi. Nejběžnější způsob pro podporu tohoto typu rozšíření je prostřednictvím doplňky (také označované jako "rozšíření" a "moduly plug-in"). Příklady reálného aplikací, které zveřejňují rozšiřitelnost s doplňky patří:  
  
-   Doplňky aplikace Internet Explorer.  
  
-   Program Windows Media Player moduly plug-in.  
  
-   Visual Studio doplňků.  
  
 Například model doplňku Windows Media Player umožňuje vývojářům třetích stran k implementaci "moduly plug-in" které rozšiřují program Windows Media Player v mnoha různými způsoby, včetně vytváření dekodérů a kodéry pro formátů médií, které nativně nepodporují Windows Přehrávač médií (například DVD, MP3), zvuk efekty a vzhledy. Každý model doplňku vychází ke zpřístupnění funkcí, které jsou jedinečné pro aplikace, i když je několik entit a chování, které jsou společné pro všechny modely doplňku.  
  
 Jsou tři hlavní entity typické doplňku rozšíření řešení *kontrakty*, *doplňky*, a *hostování aplikací*. Kontrakty definovat, jak doplňky integrovat hostování aplikací dvěma způsoby:  
  
-   Doplňky integrovat s funkcí, které je implementováno modulem hostování aplikací.  
  
-   Hostování aplikací vystavit funkcionalitu pro doplňky pro integraci se službou.  
  
 V pořadí pro doplňky má být použit potřebují hostitele aplikací je najít a je načíst za běhu. Aplikace, které podporují doplňky v důsledku toho mají tyto další funkce:  
  
-   **Zjišťování**: hledání doplňky, které dodržovat kontrakty nepodporuje hostování aplikací.  
  
-   **Aktivace**: načítání, spuštěná a navazování komunikace s moduly.  
  
-   **Izolace**: vytvoření hranice izolace, které chrání aplikace z potenciální problémy zabezpečení a spuštění s doplňky pomocí aplikační domény nebo procesy.  
  
-   **Komunikace**: povolení doplňky a hostiteli pro komunikaci mezi sebou napříč hranicemi izolace voláním metody a předávání dat aplikací.  
  
-   **Správa životního cyklu**: načítání a uvolnění domény aplikace a procesy způsobem vyčistit, předvídatelný (viz [aplikační domény](../../../../docs/framework/app-domains/application-domains.md)).  
  
-   **Správa verzí**: zajistíte, že hostovat aplikace a doplňky stále komunikovat při vytvoření nových verzí buď.  
  
 Nakonec vývoj robustní model doplňku je netriviální podniku. Z tohoto důvodu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytuje infrastrukturu pro vytváření modelů doplňku.  
  
> [!NOTE]
>  Podrobnější informace o doplňcích, najdete v části [doplňky a rozšíření](../../../../docs/framework/add-ins/index.md).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>Přehled modelu doplňku rozhraní .NET framework  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Doplňku modelu v nalezen <xref:System.AddIn> obor názvů, obsahuje sadu typy, které jsou navržené tak zjednodušit vývoj doplňku rozšíření. Základní jednotka [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model doplňku *kontrakt*, která definuje, jak hostitelskou aplikaci a doplněk vzájemně komunikovat. Hostitelskou aplikaci pomocí na hostiteli specifické pro aplikaci zpřístupněn kontraktu *zobrazení* kontraktu. Podobně přidat v konkrétní *zobrazení* kontraktu je zpřístupněné pro doplněk. *Adaptér* používá k povolení hostitele aplikací a doplněk ke komunikaci mezi jejich příslušné zobrazení kontraktu. Kontrakty, zobrazení a adaptéry jsou označovány jako segmenty, a představuje sadu související segmentů *kanálu*. Kanály jsou foundation, na kterém [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku modelu podporuje zjišťování, aktivace, izolace zabezpečení, izolace provedení (s použitím domény aplikace a procesy), komunikace, správu životního cyklu a správu verzí.  
  
 Součet této podpory umožňuje vývojářům vytvářet doplňky, které se integrují s funkcemi hostitelskou aplikaci. Ale některé scénáře vyžadují hostování aplikací zobrazíte [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] poskytované doplňků. Protože každý technologie prezentace v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] má svou vlastní model pro implementaci [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku model nepodporuje žádné konkrétní prezentace technologie. Místo toho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] přidat model s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] podporu pro doplňky.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>Doplňky WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ve spojení s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku modelu, můžete k vyřešení širokou škálu scénářů, které vyžadují hostitele aplikací zobrazíte [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] z doplňků. Konkrétně tyto scénáře jsou používala [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] s následující dva programovací modely:  
  
1.  **Doplněk vrátí uživatelského rozhraní**. Doplněk, vrátí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] hostitelské aplikaci prostřednictvím volání metody, jak jsou definovány ve smlouvě. Tento scénář se používá v následujících případech:  
  
    -   Vzhled [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , je vrácen rutinou doplněk je závislá na buď dat nebo podmínek, které existují pouze v době běhu, jako například dynamicky generované sestavy.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Služeb poskytovaných doplněk, se liší od [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z hostitele aplikací, které můžete použít doplněk.  
  
    -   Doplněk především provádí služba pro hostitelskou aplikaci a sestavy stavu pro hostitele aplikace s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
2.  **Doplněk je uživatelské rozhraní**. Doplněk je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], podle definice kontraktu. Tento scénář se používá v následujících případech:  
  
    -   Doplněk neposkytuje služby, než se zobrazuje, jako je například oznámení o inzerovaném programu.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Služeb poskytovaných doplněk je společné pro všechny hostitele aplikace, které můžete použít tento doplněk, jako je kalkulačky nebo volby barev.  
  
 Tyto scénáře vyžadují, aby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] objekty lze předat mezi hostitele aplikací a doplňku aplikační domény. Vzhledem k tomu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku modelu spoléhá na vzdálenou komunikaci pro komunikaci mezi doménami aplikací, tyto objekty, které se předávají mezi nimi musí být učinit vzdáleným.  
  
 Objekt učinit vzdáleným je instance třídy, která nepodporuje jeden nebo více následujících akcí:  
  
-   Odvozená z <xref:System.MarshalByRefObject> třídy.  
  
-   Implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
-   Má <xref:System.SerializableAttribute> atribut použitý.  
  
> [!NOTE]
>  Další informace týkající se vytváření učinit vzdáleným [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty, najdete v části [provedení učinit vzdáleným objekty](http://msdn.microsoft.com/en-us/01197253-3f13-43b7-894d-9683e431192a).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Typy nejsou učinit vzdáleným. K vyřešení problému, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model doplňku povolit [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vytvořené doplňky zobrazený z hostitele aplikací. Tato podpora je k dispozici ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dva typy: <xref:System.AddIn.Contract.INativeHandleContract> rozhraní a dvě statické metody implementované <xref:System.AddIn.Pipeline.FrameworkElementAdapters> – třída: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Na vysoké úrovni se používají tyto typy a metody následujícím způsobem:  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]vyžaduje, aby [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] poskytované doplňky jsou třídy, které jsou odvozeny od přímo nebo nepřímo <xref:System.Windows.FrameworkElement>, jako jsou například tvarů, ovládací prvky, uživatelských ovládacích prvků, panelů rozložení a stránky.  
  
2.  Bez ohledu na kontrakt deklaruje, že uživatelského rozhraní se předají mezi doplněk a hostitelskou aplikaci, musí být deklarována jako <xref:System.AddIn.Contract.INativeHandleContract> (ne <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> je učinit vzdáleným reprezentace doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , může být předán přes hranice izolace.  
  
3.  Před předáním z v doplňku na domény aplikace <xref:System.Windows.FrameworkElement> zabalený jako <xref:System.AddIn.Contract.INativeHandleContract> voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Po předávány do domény aplikace hostitelskou aplikaci, <xref:System.AddIn.Contract.INativeHandleContract> musí být vytvořen nový balíček <xref:System.Windows.FrameworkElement> voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Jak <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> používají závisí na konkrétní scénář. Následující části obsahují podrobnosti pro každou programovací model.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>Doplněk vrátí uživatelské rozhraní  
 Pro doplněk vrátit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do hostitele aplikace, vyžadují se následující věci:  
  
1.  Hostitelskou aplikaci a kanálu musí být vytvořen, protože popsaného [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [doplňky a rozšíření](../../../../docs/framework/add-ins/index.md) dokumentaci.  
  
2.  Kontrakt musí implementovat <xref:System.AddIn.Contract.IContract> a vrátit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], kontrakt, musí deklarovat metodu s návratovou hodnotou typu <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Předá mezi doplněk a hostitelem aplikace přímo nebo nepřímo, pocházet z <xref:System.Windows.FrameworkElement>.  
  
4.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , Je vrácen rutinou doplněk převést z <xref:System.Windows.FrameworkElement> k <xref:System.AddIn.Contract.INativeHandleContract> před překračuje hranice izolace.  
  
5.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , Je vrácena, musíte převést z <xref:System.AddIn.Contract.INativeHandleContract> k <xref:System.Windows.FrameworkElement> po překročení meze hranice izolace.  
  
6.  Hostitelskou aplikaci zobrazí vrácený <xref:System.Windows.FrameworkElement>.  
  
 Pro příklad, který ukazuje, jak implementovat doplněk, který vrací [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], najdete v části [vytvořit doplněk, který vrací uživatelského rozhraní](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>Doplněk je uživatelské rozhraní  
 Pokud je doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], vyžadují se následující věci:  
  
1.  Hostitelskou aplikaci a kanálu musí být vytvořen, protože popsaného [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [doplňky a rozšíření](../../../../docs/framework/add-ins/index.md) dokumentaci.  
  
2.  Musí implementovat rozhraní kontraktu pro doplněk <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Doplněk, který je předán hostitelskou aplikaci přímo nebo nepřímo, pocházet z <xref:System.Windows.FrameworkElement>.  
  
4.  Doplněk převést z <xref:System.Windows.FrameworkElement> k <xref:System.AddIn.Contract.INativeHandleContract> před překračuje hranice izolace.  
  
5.  Doplněk převést z <xref:System.AddIn.Contract.INativeHandleContract> k <xref:System.Windows.FrameworkElement> po překročení meze hranice izolace.  
  
6.  Hostitelskou aplikaci zobrazí vrácený <xref:System.Windows.FrameworkElement>.  
  
 Pro příklad, který ukazuje, jak implementovat doplněk, který je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], najdete v části [vytvoření uživatelského rozhraní Add-In tedy](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Vrácení více uživatelská z doplňku  
 Doplňky často nabízí více [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] pro hostování aplikací k zobrazení. Představte si třeba doplněk, který je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] také poskytující informace o stavu do aplikace hostitele také jako [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Doplněk takto můžete implementovat pomocí kombinace postupů z obou [Add-In vrátí uživatele rozhraní](#ReturnUIFromAddInContract) a [Add-In je uživatel rozhraní](#AddInIsAUI) modelů.  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>Doplňky a aplikace prohlížeče XAML  
 V příkladech, pokud hostitelskou aplikaci byl nainstalovaný samostatné aplikace. Ale [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] můžou hostovat taky doplňky, i když se následující další požadavky na sestavení a implementace:  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Manifest aplikace musí být nakonfigurován speciálně pro stažení kanálu (složky a sestavení) a přidejte sestavení do [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] mezipaměť aplikací v klientském počítači, ve stejné složce jako [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Musíte použít kód zjišťovat a načíst doplňků [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] mezipaměť aplikací pro [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jako umístění kanálu a doplněk.  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Musí načíst doplněk do kontextu zabezpečení speciální Pokud doplněk odkazuje volné soubory, které jsou umístěny v lokalitě původu; Pokud je hostováno pomocí [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], doplňky může odkazovat pouze na volné soubory, které jsou umístěny na serveru hostitele aplikace původu.  
  
 Tyto úkoly popisují podrobně v následující témata.  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Konfigurace kanálu a Add-In pro nasazení pomocí technologie ClickOnce  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]je stažen do a spusťte ze složky bezpečné v [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nasazení mezipaměti. Aby [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] k hostování v, je nutné stáhnout sestavení kanálu a doplněk ke složce bezpečné. To můžete udělat, musíte nakonfigurovat manifest aplikace zahrnuje kanálu a sestavení doplňku pro stahování. Děje se tak snadno [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], i když kanálu a přidat v sestavení musí být na hostiteli [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu kořenovou složku v pořadí pro [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] ke zjištění sestavení kanálu.  
  
 V důsledku toho prvním krokem je vytvoření kanálu a doplňku sestavení [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kořenové projektu nastavením jeho výstup každé kanálu sestavení a doplněk sestavení projektů. Následující tabulka uvádí výstupní cesta sestavení kanálu sestavení projektů a doplňku sestavení projektu nacházejí ve stejné složce řešení a kořenový jako hostitel [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu.  
  
 Tabulka 1: Vytvoření výstupní cesta pro kanál sestavení, které jsou hostované XBAP  
  
|Kanál sestavení projektu|Vytvoření výstupní cesta|  
|-------------------------------|-----------------------|  
|Kontrakt|`..\HostXBAP\Contracts\`|  
|Přidejte v zobrazení|`..\HostXBAP\AddInViews\`|  
|Přidat straně adaptéru|`..\HostXBAP\AddInSideAdapters\`|  
|Adaptér na straně hostitele|`..\HostXBAP\HostSideAdapters\`|  
|Add-In|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 Dalším krokem je určení kanálu sestavení a sestavení doplňku jako [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] obsahu souborů v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] provedením následujících akcí:  
  
1.  Včetně kanálu a doplněk sestavení v projektu pravým tlačítkem myši na každý kanál složky v Průzkumníku řešení a zvolením **zahrnout do projektu**.  
  
2.  Nastavení **akce sestavení** pro každé sestavení kanálu a sestavení doplňku pro **obsahu** z **vlastnosti** okno.  
  
 Posledním krokem je konfigurace manifest aplikace zahrnuje soubory sestavení kanálu a soubor doplňku sestavení pro stahování. Soubory se musí nacházet ve složkách v kořenové složce v [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] mezipaměti, který [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] zabírá aplikace. Konfigurace lze dosáhnout v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] provedením následujících akcí:  
  
1.  Klikněte pravým tlačítkem myši [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu, klikněte na tlačítko **vlastnosti**, klikněte na tlačítko **publikovat**a potom klikněte na **soubory aplikace** tlačítko.  
  
2.  V **soubory aplikace** dialogové okno, sada **stav publikování** jednotlivých kanálu a knihovny DLL pro doplněk **zahrnout (automaticky)**a nastavte **Skupina stažení** pro každý kanál a přidejte DLL k **(povinné)**.  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Použití kanálu a doplněk od základní aplikace  
 Když jsou kanálu a jsou nakonfigurovaní pro [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nasazení, se stáhnou do stejné [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] složky mezipaměti jako [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Použití kanálu a doplňky [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kódu musí je můžete získat z aplikace základní. Různé typy a členy [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model doplňku pro použití kanálů a doplňky poskytovat zvláštní podporu pro tento scénář. Za prvé, je identifikovaný cestu <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> hodnota výčtu. Použijte tuto hodnotu s přetížení členy příslušné doplňku pro práci s kanály, které zahrnují následující:  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Přístup k serveru hostitele původu  
 Aby se zajistilo, že doplněk, můžete odkazovat soubory z lokality původu, doplněk musí být načteny izolace zabezpečení, který je ekvivalentní pro hostitelskou aplikaci. Tato úroveň zabezpečení je identifikována <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> hodnota výčtu a předána <xref:System.AddIn.Hosting.AddInToken.Activate%2A> metoda doplňku při aktivaci.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>Architektura doplňků WPF  
 Na nejvyšší úrovni jak jste viděli, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňky implementovat [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] (které jsou odvozeny přímo nebo nepřímo ze <xref:System.Windows.FrameworkElement>) pomocí <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Výsledkem je, že se vrátí hostitelskou aplikaci <xref:System.Windows.FrameworkElement> , budou zobrazena ze [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v hostitelskou aplikaci.  
  
 Pro jednoduché [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] doplňku scénáře, to je množství podrobností musí vývojář. Složitější scénáře, hlavně pokud, vyzkoušejte využívat další [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] služeb, jako je rozložení, prostředky a datové vazby, podrobnější informace o postupu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] přidat model s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Podpora je potřeba pochopit, její výhody a omezení.  
  
 Zásadně [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] neprojde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z doplňku pro hostitelskou aplikaci; místo toho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] předá popisovač okna Win32 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] interoperability. Jako takový, když [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z doplňku předaný hostitelskou aplikaci, dojde k následujícímu:  
  
-   Na straně doplňku [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] získá popisovač okna pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] které se bude zobrazovat hostitelskou aplikaci. Popisovač okna je zapouzdřené pomocí interní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] třídu odvozenou od <xref:System.Windows.Interop.HwndSource> a implementuje <xref:System.AddIn.Contract.INativeHandleContract>. Instance této třídy je vrácen rutinou <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> a je z doplňku pro doménu aplikace zařazené do domény aplikace hostitelskou aplikaci.  
  
-   Na straně hostitele aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] znovu zabalí a <xref:System.Windows.Interop.HwndSource> jako interní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] třídu odvozenou od <xref:System.Windows.Interop.HwndHost> a odebírá <xref:System.AddIn.Contract.INativeHandleContract>. Instance této třídy je vrácen rutinou <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> pro hostitelskou aplikaci.  
  
 <xref:System.Windows.Interop.HwndHost>existuje zobrazíte [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], identifikovaný popisovače oken z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Další informace najdete v tématu [WPF a vzájemná spolupráce Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
 Souhrnně <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> existovat umožňující popisovač okna pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] mají být předány z doplňku hostitelskou aplikaci, kde je zapouzdřené pomocí <xref:System.Windows.Interop.HwndHost> a zobrazí hostitele aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  Protože získá hostitelskou aplikaci <xref:System.Windows.Interop.HwndHost>, hostitelskou aplikaci nelze převést objekt, který je vrácen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> na typ se implementují jako doplněk (například <xref:System.Windows.Controls.UserControl>).  
  
 Svou povahou <xref:System.Windows.Interop.HwndHost> má určitá omezení, které mají vliv jak hostovat aplikace lze využít. Ale [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje <xref:System.Windows.Interop.HwndHost> s několik možností pro scénáře doplňku. Dále jsou uvedená tyto výhody a omezení.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>WPF doplňku výhody  
 Protože [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] doplňku [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] se zobrazí z hostitele aplikací pomocí interní třída odvozená z <xref:System.Windows.Interop.HwndHost>, které [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] jsou omezené možnosti <xref:System.Windows.Interop.HwndHost> s ohledem na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] službám, jako je rozložení, vykreslování, vazby dat, styly, šablony a prostředky. Ale [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje jeho vnitřní <xref:System.Windows.Interop.HwndHost> podtřídami s další funkce, které zahrnují následující:  
  
-   Přecházení mezi hostitelskou aplikaci pomocí tabulátoru [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Všimněte si, že "add-in [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programovací model vyžaduje adaptér přidat straně přepsat <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> povolit procházení tabulátorem, zda doplněk je plně důvěryhodné nebo částečně důvěryhodný.  
  
-   Aby byla dodržena požadavky na usnadnění přístupu pro add-in [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] , se zobrazí z hostitelskou aplikaci [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
-   Povolení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacím spouštění bezpečně ve scénářích s více domény aplikace.  
  
-   Brání Neplatný přístup k doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] okno zpracovává při spuštění doplňků izolace zabezpečení (tedy karantény částečným vztahem důvěryhodnosti zabezpečení). Volání metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> zajišťuje tento zabezpečení:  
  
    -   Pro "doplněk vrátí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programovací model, jediný způsob, jak předat popisovač okna pro doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] napříč izolaci hranic je volání <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   Pro "add-in [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programování modelu, přepsání <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> na adaptéru přidat straně a volání <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (jak je znázorněno v předchozích ukázkách) je nutné, jako je volání adaptéru přidat straně `QueryContract` implementace z adaptéru straně hostitele.  
  
-   Poskytuje více ochrana spuštění domény aplikace. Kvůli omezení s aplikační domény neošetřených výjimek, které jsou vyvolány v doplňku aplikační domény způsobit chyby, bude celá aplikace, i když existuje hranic izolace. Ale [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model doplňku poskytují jednoduchý způsob, jak tento problém obejít a zlepšení stability aplikace. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] doplňku zobrazí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vytvoří <xref:System.Windows.Threading.Dispatcher> pro vlákno, které domény aplikace spustí, pokud je hostitelskou aplikaci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace. Můžete zjistit všechny neošetřených výjimek, které v doméně aplikace provádí zpracování <xref:System.Windows.Threading.Dispatcher.UnhandledException> události [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] doplňku <xref:System.Windows.Threading.Dispatcher>. Můžete získat <xref:System.Windows.Threading.Dispatcher> z <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> vlastnost.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>WPF doplňku omezení  
 Nad rámec výhody, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] přidá do výchozí chování poskytl <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>a popisovače oken, existují také omezení pro add-in [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] , se zobrazí z hostitele aplikací:  
  
-   Doplněk [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] zobrazí z hostitele aplikací nerespektují chování výstřižek hostitelskou aplikaci.  
  
-   Koncept *vzdušného prostoru* ve vzájemné funkční spolupráci scénáře platí také pro doplňky (viz [oblasti Přehled technologie](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)).  
  
-   Hostitelskou aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] služby, jako je prostředků dědičnost, datové vazby a tvorba příkazů, nejsou automaticky k dispozici pro doplněk [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. K poskytování těchto služeb v doplňku, musíte aktualizovat kanál.  
  
-   Doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nemůže být otáčet, škálovat, nesouměrně rozdělí, vliv na jeden nebo jinak transformace (viz [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)).  
  
-   Obsahu uvnitř doplňku [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] který je vykreslen metodou kreslení operací <xref:System.Drawing> obor názvů může zahrnovat prolnutí alfa. Však obě doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a hostitelskou aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] obsahující ho musí být 100 % neprůhledné; jinými slovy, `Opacity` vlastnost na obou musí být nastavena na hodnotu 1.  
  
-   Pokud <xref:System.Windows.Window.AllowsTransparency%2A> vlastnost časového období v hostitelskou aplikaci, která obsahuje doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je nastaven na `true`, doplněk je neviditelná. To platí i v případě doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je 100 % neprůhledné (tedy `Opacity` vlastnost má hodnotu 1).  
  
-   Doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musí se zobrazují nad dalších [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementů v rámci stejného časového období nejvyšší úrovně.  
  
-   Žádná část doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] může být vykreslen pomocí <xref:System.Windows.Media.VisualBrush>. Místo toho doplněk může pořízení snímku vygenerovaného [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vytvoření rastrového obrázku, který se dá předat do hostitelskou aplikaci pomocí metody definované kontrakt.  
  
-   Mediální soubory nelze přehrát ze <xref:System.Windows.Controls.MediaElement> v doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Myš události generované pro doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jsou přijata ani aktivováno hostitelskou aplikaci a `IsMouseOver` vlastnost pro hostitelskou aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] má hodnotu `false`.  
  
-   Při deaktivaci mezi ovládacími prvky v doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], `GotFocus` a `LostFocus` události jsou přijata ani aktivováno hostitelskou aplikaci.  
  
-   Část hostitelskou aplikaci, která obsahuje doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se zobrazí bílé při tisku.  
  
-   Všechny dispečerů (viz <xref:System.Windows.Threading.Dispatcher>) Autor doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musí být vypnuté ručně před doplněk vlastníka je odpojen, pokud hostitelskou aplikaci pokračuje v provádění. Smlouvy můžete implementovat metody, které umožňují hostitelskou aplikaci signál doplněk před doplněk je odpojen, a tím umožní doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vypnout jeho dispečerů.  
  
-   Pokud doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je <xref:System.Windows.Controls.InkCanvas> nebo obsahuje <xref:System.Windows.Controls.InkCanvas>, nelze uvolnit doplněk.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Optimalizace výkonu  
 Ve výchozím nastavení, pokud jsou použity více domén aplikací různých [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sestavení vyžaduje každý aplikace jsou všechny načteno do domény této aplikace. Čas potřebný k vytvoření nové domény aplikace a spuštění aplikace v nich v důsledku toho může ovlivnit výkon. Ale [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytuje způsob, jak můžete omezit tím, že aplikace pro sdílení sestavení napříč doménami aplikací, pokud jsou již načíst instruující času zahájení. Můžete to provést pomocí <xref:System.LoaderOptimizationAttribute> atribut, který se musí použít metodu vstupního bodu (`Main`). V takovém případě je nutné použít pouze kód implementovat vaše definice aplikace (viz [přehled správy aplikací](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.LoaderOptimizationAttribute>  
 [Doplňky a rozšíření](../../../../docs/framework/add-ins/index.md)  
 [Aplikační domény](../../../../docs/framework/app-domains/application-domains.md)  
 [Přehled vzdálené komunikace rozhraní .NET framework](http://msdn.microsoft.com/en-us/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [Provedení učinit vzdáleným objekty](http://msdn.microsoft.com/en-us/01197253-3f13-43b7-894d-9683e431192a)  
 [Témata s postupy](../../../../docs/framework/wpf/app-development/how-to-topics.md)
