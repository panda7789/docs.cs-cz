---
title: Použití automatizace uživatelského rozhraní pro automatizované testování
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: ccc0f5e4172a61370c0e5a6333094dc44640b758
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040318"
---
# <a name="using-ui-automation-for-automated-testing"></a>Použití automatizace uživatelského rozhraní pro automatizované testování
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Tento přehled popisuje, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jak lze využít jako rozhraní pro programový přístup v rámci automatizovaných testovacích scénářů.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje jednotný objektový model, který umožňuje všem [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] rozhraním zpřístupnit složitou a bohatou funkcionalitu v přístupném a snadno automatizovaném způsobu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]byla vyvinuta jako nástupce Microsoft Active Accessibility. Aktivní přístupnost je stávající architektura navržená tak, aby poskytovala řešení pro zpřístupnění ovládacích prvků a aplikací. Aktivní přístupnost není navržená pomocí automatizace testů, i když se do této role vyvinula z důvodu velmi podobných požadavků usnadnění přístupu a automatizace. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Kromě poskytování přesnější řešení pro usnadnění je konkrétně navrženo tak, aby poskytovalo robustní funkce pro automatizované testování. Aktivní přístupnost například spoléhá na jedno rozhraní, aby vystavoval informace o uživatelském rozhraní a shromáždila informace vyžadované v produktech. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] odděluje dva modely.  
  
 Zprostředkovatel i klient musí implementovat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , aby mohl být užitečný jako Automatizovaný testovací nástroj. Zprostředkovatelé automatizace uživatelského rozhraní jsou aplikace, jako je Microsoft Word, Excel a další aplikace nebo ovládací prvky třetích stran založené [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] na operačním systému. Mezi klienty automatizace uživatelského rozhraní patří automatizované testovací skripty a aplikace technologie pro usnadnění.  
  
> [!NOTE]
> Záměrem tohoto přehledu je prezentovat nové a vylepšené funkce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]automatizovaného testování. Tento přehled není určený k poskytování informací o funkcích usnadnění a nebude řešit přístupnost jiným způsobem, než v případě potřeby.  
  
## <a name="ui-automation-in-a-provider"></a>Automatizace uživatelského rozhraní ve zprostředkovateli  
 Aby bylo možné automatizovat, vývojář aplikace nebo ovládacího prvku musí zjistit, jaké akce může koncový uživatel provádět [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na objektu pomocí standardní interakce klávesnice a myši. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]  
  
 Jakmile jsou tyto klíčové akce identifikovány, měly by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] být v ovládacím prvku implementovány odpovídající vzory ovládacích prvků (tj. vzory ovládacích prvků, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] které zrcadlí funkce a chování elementu). Například interakce uživatele s ovládacím prvkem pole se seznamem (například dialog Spustit) obvykle zahrnuje rozbalení a sbalení pole se seznamem pro skrytí nebo zobrazení seznamu položek, výběr položky z tohoto seznamu nebo přidání nové hodnoty prostřednictvím vstupu z klávesnice.  
  
> [!NOTE]
> S jinými modely usnadnění musí vývojáři shromažďovat informace přímo z jednotlivých tlačítek, nabídek nebo jiných ovládacích prvků. Každý typ ovládacího prvku bohužel přichází v desítkách malých variant. Jinými slovy, i když deset variací (pushbutton) může fungovat stejným způsobem a provádět stejnou funkci, musí být všechny zpracovány jako jedinečné ovládací prvky. Neexistuje žádný způsob, jak zjistit, že tyto ovládací prvky jsou funkčně ekvivalentní. Byly vyvinuty vzory ovládacích prvků, které by představovaly toto chování obecného ovládacího prvku. Další informace najdete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
### <a name="implementing-ui-automation"></a>Implementace automatizace uživatelského rozhraní  
 Jak bylo zmíněno dříve, bez sjednoceného modelu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], který je poskytován nástrojem, je nutné, aby testovací nástroje a vývojáři znali informace specifické pro rozhraní, aby bylo možné vystavit vlastnosti a chování ovládacích prvků v daném rozhraní. Vzhledem k tomu, že v operačních systémech Windows může být v jednom okamžiku k dispozici několik různých rozhraní [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]uživatelského [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]rozhraní, včetně, a Windows Presentation Foundation (WPF), může to být úkol těžké k testování více aplikací s ovládací prvky, které vypadají podobně. Například následující tabulka popisuje názvy vlastností specifické pro rozhraní, které jsou nutné k načtení názvu (nebo textu) přidruženého k ovládacímu prvku tlačítko a zobrazení jediné ekvivalentní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti.  
  
|Typ ovládacího prvku automatizace uživatelského rozhraní|Architektura uživatelského rozhraní|Vlastnost specifická pro rozhraní|Vlastnost automatizace uživatelského rozhraní|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Tlačítko|Windows Presentation Foundation|Obsah|NameProperty|  
|Tlačítko|Win32|Titulek|NameProperty|  
|Image|HTML|ALT|NameProperty|  
  
 Zprostředkovatelé automatizace uživatelského rozhraní zodpovídají za mapování vlastností konkrétního rozhraní na odpovídající [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti.  
  
 Informace o implementaci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve zprostředkovateli najdete v [poskytovatelích automatizace uživatelského rozhraní pro spravovaný kód](ui-automation-providers-for-managed-code.md). Informace o implementaci vzorů ovládacích prvků jsou k dispozici v vzorcích [ovládacího prvku automatizace uživatelského rozhraní](ui-automation-control-patterns.md) a v [textovém vzoru automatizace uživatelského rozhraní](ui-automation-text-pattern.md).  
  
## <a name="ui-automation-in-a-client"></a>Automatizace uživatelského rozhraní v klientovi  
 Cílem mnoha automatizovaných testovacích nástrojů a scénářů je konzistentní a opakující se manipulace s uživatelským rozhraním. To může zahrnovat konkrétní ovládací prvky pro testování částí až po nahrávání a přehrávání testovacích skriptů, které procházejí řadou obecných akcí ve skupině ovládacích prvků.  
  
 Komplikace, která nastane z automatizovaných aplikací, je obtížnost synchronizace testu s dynamickým cílem. Například ovládací prvek seznamu, který je součástí Správce úloh systému Windows, zobrazuje seznam aktuálně spuštěných aplikací. Vzhledem k tomu, že položky v poli se seznamem se dynamicky aktualizují mimo ovládací prvek testovací aplikace, pokus o opakování výběru konkrétní položky v seznamu s jakoukoliv konzistencí není možný. K podobným problémům může také dojít při pokusu o zopakování jednoduchých změn fokusu v rámci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , který je mimo ovládací prvek testovací aplikace.  
  
### <a name="programmatic-access"></a>Programový přístup  
 Programový přístup poskytuje možnost napodobeniny, prostřednictvím kódu, jakékoliv interakce a zkušeností vystavené tradičním vstupem myši a klávesnicí. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umožňuje programový přístup prostřednictvím pěti součástí:  
  
- Strom usnadňuje navigaci prostřednictvím struktury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom je sestaven z kolekce objektu hWnd. Další informace najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md) .  
  
- Prvky automatizace jsou jednotlivé komponenty v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Tyto informace mohou být často podrobnější než hWnd. Další informace najdete v tématu [Přehled typů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-types-overview.md).  
  
- Vlastnosti služby Automation poskytují konkrétní informace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] o prvcích. Další informace najdete v tématu [Přehled vlastností automatizace uživatelského rozhraní](ui-automation-properties-overview.md).  
  
- Vzory ovládacích prvků definují konkrétní aspekt funkcí ovládacího prvku; můžou se skládat z informací o vlastnostech, metodách, událostech a strukturách. Další informace najdete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
- Události automatizace poskytují oznámení a informace o událostech. Další informace najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
### <a name="key-properties-for-test-automation"></a>Klíčové vlastnosti pro automatizaci testů  
 Schopnost jedinečně identifikovat a následně najít libovolný ovládací prvek v rámci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] poskytuje základ pro automatizované testovací aplikace, které na to [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]budou fungovat. Existuje několik [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vlastností používaných klienty a zprostředkovateli, kteří to pomáhají.  
  
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
|Přidejte odkazy na automatizaci uživatelského rozhraní.|Tady je seznam knihoven DLL potřebných pro klienty automatizace uživatelského rozhraní. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<br /><br /> – UIAutomationClient. dll poskytuje přístup k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rozhraním API na straně klienta.<br />-UIAutomationClientSideProvider. dll nabízí možnost automatizace [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládacích prvků. Viz [Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky](ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes. dll poskytuje přístup ke konkrétním typům definovaným [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]v.|  
|<xref:System.Windows.Automation> Přidejte obor názvů.|Tento obor názvů obsahuje všechny klienty automatizace uživatelského rozhraní, musí používat možnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s výjimkou zpracování textu.|  
|<xref:System.Windows.Automation.Text> Přidejte obor názvů.|Tento obor názvů obsahuje všechno, co Klienti automatizace uživatelského rozhraní potřebují k použití [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] možností zpracování textu.|  
|Najít ovládací prvky, které vás zajímají|Skripty automatizovaného testu vyhledají prvky automatizace uživatelského rozhraní, které reprezentují ovládací prvky zájmu v rámci stromu automatizace.<br /><br /> Existuje několik způsobů, jak získat prvky automatizace uživatelského rozhraní s kódem.<br /><br /> -Dotazování [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Automation.Condition> pomocí příkazu. Obvykle se používá jazykově neutrální <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> . **Poznámka:**  Lze získat pomocí nástroje, jako je například zkontrolovat. exe, který je schopen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] itemize vlastnosti ovládacího prvku. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> <br /><br /> – K procházení <xref:System.Windows.Automation.TreeWalker> celého [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu nebo jeho podmnožiny použijte třídu.<br />– Sledovat fokus.<br />– Použijte hWnd ovládacího prvku.<br />– Použijte umístění obrazovky, například umístění kurzoru myši.<br /><br /> Viz [získání prvků automatizace uživatelského rozhraní](obtaining-ui-automation-elements.md)|  
|Získání vzorů ovládacích prvků|Vzory ovládacích prvků zpřístupňují běžné chování pro funkčně podobné ovládací prvky.<br /><br /> Po vyhledání ovládacích prvků, které vyžadují testování, budou automatizované testovací skripty získávat řídicí vzory z těchto prvků automatizace uživatelského rozhraní. Například <xref:System.Windows.Automation.InvokePattern> vzor ovládacího prvku pro typickou funkčnost tlačítka <xref:System.Windows.Automation.WindowPattern> nebo vzor ovládacího prvku pro funkci okna.<br /><br /> Viz [Přehled vzorců ovládacího prvku automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).|  
|Automatizace uživatelského rozhraní|Skripty automatizovaného testu teď můžou řídit [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jakýkoli z těchto údajů [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] z rozhraní, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a to pomocí informací a funkcí zveřejněných vzory ovládacích prvků.|  
  
## <a name="related-tools-and-technologies"></a>Související nástroje a technologie  
 K dispozici je řada souvisejících nástrojů a technologií, které podporují automatizované testování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]pomocí nástroje.  
  
- Kontrola. exe je aplikace grafického uživatelského rozhraní (GUI), kterou lze použít ke shromažďování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informací jak pro vývoj, tak pro vývoj a ladění klienta. Kontrola. exe je součástí Windows SDK.  
  
- MSAABridge zpřístupňuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informace pro aktivní klienty přístupnosti. Primárním cílem přemostění [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] na aktivní přístupnost je umožnit stávajícím klientům aktivních usnadnění pracovat s jakýmkoli implementací [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní.  
  
## <a name="security"></a>Zabezpečení  
 Informace o zabezpečení najdete v tématu [Přehled zabezpečení automatizace uživatelského rozhraní](ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Principy automatizace uživatelského rozhraní](index.md)
