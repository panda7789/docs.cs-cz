---
title: Použití automatizace uživatelského rozhraní pro automatizované testování
description: Přečtěte si přehled, který popisuje, jak používat automatizaci uživatelského rozhraní jako architekturu pro programový přístup v rámci automatizovaných testovacích scénářů.
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: a38efd30e6f7f4cd05664d847c525dcf59ded61a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924471"
---
# <a name="using-ui-automation-for-automated-testing"></a>Použití automatizace uživatelského rozhraní pro automatizované testování
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Tento přehled popisuje [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , jak lze využít jako rozhraní pro programový přístup v rámci automatizovaných testovacích scénářů.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje jednotný objektový model, který umožňuje všem [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] rozhraním zpřístupnit složitou a bohatou funkcionalitu v přístupném a snadno automatizovaném způsobu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]byla vyvinuta jako nástupce Microsoft Active Accessibility. Aktivní přístupnost je stávající architektura navržená tak, aby poskytovala řešení pro zpřístupnění ovládacích prvků a aplikací. Aktivní přístupnost není navržená pomocí automatizace testů, i když se do této role vyvinula z důvodu velmi podobných požadavků usnadnění přístupu a automatizace. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Kromě poskytování přesnější řešení pro usnadnění je konkrétně navrženo tak, aby poskytovalo robustní funkce pro automatizované testování. Aktivní přístupnost například spoléhá na jedno rozhraní, aby vystavoval informace o uživatelském rozhraní a shromáždila informace vyžadované v produktech. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]odděluje dva modely.  
  
 Zprostředkovatel i klient musí implementovat, aby [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mohl být užitečný jako Automatizovaný testovací nástroj. Zprostředkovatelé automatizace uživatelského rozhraní jsou aplikace, jako je Microsoft Word, Excel a další aplikace nebo ovládací prvky třetích stran založené na operačním systému Microsoft Windows. Mezi klienty automatizace uživatelského rozhraní patří automatizované testovací skripty a aplikace technologie pro usnadnění.  
  
> [!NOTE]
> Záměrem tohoto přehledu je prezentovat nové a vylepšené funkce automatizovaného testování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Tento přehled není určený k poskytování informací o funkcích usnadnění a nebude řešit přístupnost jiným způsobem, než v případě potřeby.  
  
## <a name="ui-automation-in-a-provider"></a>Automatizace uživatelského rozhraní ve zprostředkovateli  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]Aby bylo možné automatizovat, vývojář aplikace nebo ovládacího prvku musí zjistit, jaké akce může koncový uživatel provádět na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] objektu pomocí standardní interakce klávesnice a myši.  
  
 Jakmile jsou tyto klíčové akce identifikovány, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] měly by být v ovládacím prvku implementovány odpovídající vzory ovládacích prvků (tj. vzory ovládacích prvků, které zrcadlí funkce a chování elementu). Například interakce uživatele s ovládacím prvkem pole se seznamem (například dialog Spustit) obvykle zahrnuje rozbalení a sbalení pole se seznamem pro skrytí nebo zobrazení seznamu položek, výběr položky z tohoto seznamu nebo přidání nové hodnoty prostřednictvím vstupu z klávesnice.  
  
> [!NOTE]
> S jinými modely usnadnění musí vývojáři shromažďovat informace přímo z jednotlivých tlačítek, nabídek nebo jiných ovládacích prvků. Každý typ ovládacího prvku bohužel přichází v desítkách malých variant. Jinými slovy, i když deset variací (pushbutton) může fungovat stejným způsobem a provádět stejnou funkci, musí být všechny zpracovány jako jedinečné ovládací prvky. Neexistuje žádný způsob, jak zjistit, že tyto ovládací prvky jsou funkčně ekvivalentní. Byly vyvinuty vzory ovládacích prvků, které by představovaly toto chování obecného ovládacího prvku. Další informace najdete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
### <a name="implementing-ui-automation"></a>Implementace automatizace uživatelského rozhraní  
 Jak bylo zmíněno dříve, bez sjednoceného modelu, který je poskytován nástrojem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , je nutné, aby testovací nástroje a vývojáři znali informace specifické pro rozhraní, aby bylo možné vystavit vlastnosti a chování ovládacích prvků v daném rozhraní. Vzhledem k tomu, že v operačních systémech Windows může být v jednom okamžiku k dispozici několik různých rozhraní uživatelského rozhraní, včetně Win32, model Windows Forms a Windows Presentation Foundation (WPF), může se jednat o úlohu těžké k otestování více aplikací s ovládacími prvky, které vypadají podobně. Například následující tabulka popisuje názvy vlastností specifické pro rozhraní, které jsou nutné k načtení názvu (nebo textu) přidruženého k ovládacímu prvku tlačítko a zobrazení jediné ekvivalentní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnosti.  
  
|Typ ovládacího prvku automatizace uživatelského rozhraní|Architektura uživatelského rozhraní|Vlastnost specifická pro rozhraní|Vlastnost automatizace uživatelského rozhraní|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Tlačítko|Windows Presentation Foundation|Obsah|NameProperty|  
|Tlačítko|Win32|Titulek|NameProperty|  
|Image|HTML|ALT|NameProperty|  
  
 Zprostředkovatelé automatizace uživatelského rozhraní zodpovídají za mapování vlastností konkrétního rozhraní na odpovídající [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnosti.  
  
 Informace o implementaci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve zprostředkovateli najdete v [poskytovatelích automatizace uživatelského rozhraní pro spravovaný kód](ui-automation-providers-for-managed-code.md). Informace o implementaci vzorů ovládacích prvků jsou k dispozici v vzorcích [ovládacího prvku automatizace uživatelského rozhraní](ui-automation-control-patterns.md) a v [textovém vzoru automatizace uživatelského rozhraní](ui-automation-text-pattern.md).  
  
## <a name="ui-automation-in-a-client"></a>Automatizace uživatelského rozhraní v klientovi  
 Cílem mnoha automatizovaných testovacích nástrojů a scénářů je konzistentní a opakující se manipulace s uživatelským rozhraním. To může zahrnovat konkrétní ovládací prvky pro testování částí až po nahrávání a přehrávání testovacích skriptů, které procházejí řadou obecných akcí ve skupině ovládacích prvků.  
  
 Komplikace, která nastane z automatizovaných aplikací, je obtížnost synchronizace testu s dynamickým cílem. Například ovládací prvek seznamu, který je součástí Správce úloh systému Windows, zobrazuje seznam aktuálně spuštěných aplikací. Vzhledem k tomu, že položky v poli se seznamem se dynamicky aktualizují mimo ovládací prvek testovací aplikace, pokus o opakování výběru konkrétní položky v seznamu s jakoukoliv konzistencí není možný. K podobným problémům může také dojít při pokusu o zopakování jednoduchých změn fokusu v rámci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , který je mimo ovládací prvek testovací aplikace.  
  
### <a name="programmatic-access"></a>Programový přístup  
 Programový přístup poskytuje možnost napodobeniny, prostřednictvím kódu, jakékoliv interakce a zkušeností vystavené tradičním vstupem myši a klávesnicí. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umožňuje programový přístup prostřednictvím pěti součástí:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom usnadňuje navigaci prostřednictvím struktury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Strom je sestaven z kolekce objektu hWnd. Další informace najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md) .  
  
- Prvky automatizace jsou jednotlivé komponenty v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Tyto informace mohou být často podrobnější než hWnd. Další informace najdete v tématu [Přehled typů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-types-overview.md).  
  
- Vlastnosti služby Automation poskytují konkrétní informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvcích. Další informace najdete v tématu [Přehled vlastností automatizace uživatelského rozhraní](ui-automation-properties-overview.md).  
  
- Vzory ovládacích prvků definují konkrétní aspekt funkcí ovládacího prvku; můžou se skládat z informací o vlastnostech, metodách, událostech a strukturách. Další informace najdete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
- Události automatizace poskytují oznámení a informace o událostech. Další informace najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
### <a name="key-properties-for-test-automation"></a>Klíčové vlastnosti pro automatizaci testů  
 Schopnost jedinečně identifikovat a následně najít libovolný ovládací prvek v rámci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] poskytuje základ pro automatizované testovací aplikace, které na to budou fungovat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Existuje několik [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vlastností používaných klienty a zprostředkovateli, kteří to pomáhají.  
  
#### <a name="automationid"></a>AutomationID  
 Jednoznačně identifikuje element automatizace ze svých sourozenců. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>není lokalizován na rozdíl od vlastnosti <xref:System.Windows.Automation.AutomationElement.NameProperty> , která je obvykle lokalizována v případě, že je produkt dodán v několika jazycích. Viz [použití vlastnosti AutomationId](use-the-automationid-property.md).  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>nezaručuje jedinečnou identitu v rámci stromu automatizace. Například aplikace může obsahovat ovládací prvek nabídky s více položkami nabídky nejvyšší úrovně, které zase mají více podřízených položek nabídky. Tyto sekundární položky nabídky mohou být identifikovány pomocí obecného schématu, jako je například "Item1 –, Item 2, Item3 – atd.", umožňující duplicitní identifikátory pro podřízené položky v rámci položek nabídky nejvyšší úrovně.  
  
#### <a name="controltype"></a>ControlType  
 Určuje typ ovládacího prvku reprezentovaný prvkem automatizace. Významné informace lze odvodit ze znalostí typu ovládacího prvku. Viz [Přehled typů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Toto je textový řetězec, který identifikuje nebo vysvětluje ovládací prvek. <xref:System.Windows.Automation.AutomationElement.NameProperty>by měla být použita s opatrností, protože může být lokalizována. Informace najdete v tématu [Přehled vlastností automatizace uživatelského rozhraní](ui-automation-properties-overview.md).  
  
### <a name="implementing-ui-automation-in-a-test-application"></a>Implementace automatizace uživatelského rozhraní v testovací aplikaci  
  
|||  
|-|-|  
|Přidejte odkazy na automatizaci uživatelského rozhraní.|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Tady je seznam knihoven DLL potřebných pro klienty automatizace uživatelského rozhraní.<br /><br /> -UIAutomationClient.dll poskytuje přístup k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rozhraním API na straně klienta.<br />-UIAutomationClientSideProvider.dll poskytuje možnost automatizovat ovládací prvky Win32. Viz [Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky](ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes.dll poskytuje přístup ke konkrétním typům definovaným v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|Přidejte <xref:System.Windows.Automation> obor názvů.|Tento obor názvů obsahuje všechny klienty automatizace uživatelského rozhraní, musí používat možnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s výjimkou zpracování textu.|  
|Přidejte <xref:System.Windows.Automation.Text> obor názvů.|Tento obor názvů obsahuje všechno, co Klienti automatizace uživatelského rozhraní potřebují k použití možností [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zpracování textu.|  
|Najít ovládací prvky, které vás zajímají|Skripty automatizovaného testu vyhledají prvky automatizace uživatelského rozhraní, které reprezentují ovládací prvky zájmu v rámci stromu automatizace.<br /><br /> Existuje několik způsobů, jak získat prvky automatizace uživatelského rozhraní s kódem.<br /><br /> -Dotazování [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pomocí <xref:System.Windows.Automation.Condition> příkazu. Obvykle se používá jazykově neutrální <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> . **Poznámka:**  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>Lze získat pomocí nástroje, například Inspect.exe, který je schopen itemize [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti ovládacího prvku. <br /><br /> – <xref:System.Windows.Automation.TreeWalker> K procházení celého [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu nebo jeho podmnožiny použijte třídu.<br />– Sledovat fokus.<br />– Použijte hWnd ovládacího prvku.<br />– Použijte umístění obrazovky, například umístění kurzoru myši.<br /><br /> Viz [získání prvků automatizace uživatelského rozhraní](obtaining-ui-automation-elements.md)|  
|Získání vzorů ovládacích prvků|Vzory ovládacích prvků zpřístupňují běžné chování pro funkčně podobné ovládací prvky.<br /><br /> Po vyhledání ovládacích prvků, které vyžadují testování, budou automatizované testovací skripty získávat řídicí vzory z těchto prvků automatizace uživatelského rozhraní. Například <xref:System.Windows.Automation.InvokePattern> vzor ovládacího prvku pro typickou funkčnost tlačítka nebo <xref:System.Windows.Automation.WindowPattern> vzor ovládacího prvku pro funkci okna.<br /><br /> Viz [Přehled vzorců ovládacího prvku automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).|  
|Automatizace uživatelského rozhraní|Skripty automatizovaného testu teď můžou řídit jakýkoli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] z těchto [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] údajů z rozhraní, a to pomocí informací a funkcí zveřejněných [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvků.|  
  
## <a name="related-tools-and-technologies"></a>Související nástroje a technologie  
 K dispozici je řada souvisejících nástrojů a technologií, které podporují automatizované testování pomocí nástroje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
- Inspect.exe je aplikace grafického uživatelského rozhraní (GUI), kterou lze použít ke shromažďování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informací jak pro vývoj, tak pro vývoj a ladění klienta. Inspect.exe je součástí Windows SDK.  
  
- MSAABridge zpřístupňuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informace pro aktivní klienty přístupnosti. Primárním cílem přemostění [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] na aktivní přístupnost je umožnit stávajícím klientům aktivních usnadnění pracovat s jakýmkoli implementací rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
## <a name="security"></a>Zabezpečení  
 Informace o zabezpečení najdete v tématu [Přehled zabezpečení automatizace uživatelského rozhraní](ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Principy automatizace uživatelského rozhraní](index.md)
