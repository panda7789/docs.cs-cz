---
title: Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: f62631a15dd348b6f6ea27a82d7b45aab92ceed2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179939"
---
# <a name="ui-automation-control-patterns-overview"></a>Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Tento přehled [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zavádí vzory ovládacích prvku. Vzory ovládacího prvku poskytují způsob kategorizace a vystavení funkce ovládacího prvku nezávisle na typu ovládacího prvku nebo vzhledovládacího prvku.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Používá vzory ovládacích prvku k reprezentaci běžného chování ovládacího prvku. Například použít invoke ovládací prvek vzor pro ovládací prvky, které lze vyvolat (například tlačítka) a Scroll ovládací prvek vzor pro ovládací prvky, které mají posuvníky (například seznamy, zobrazení seznamu nebo pole se seznamem). Vzhledem k tomu, že každý vzor ovládacího prvku představuje samostatnou funkci, lze je kombinovat k popisu úplné sady funkcí podporovaných určitým ovládacím prvkem.  
  
> [!NOTE]
> Agregační ovládací prvky – [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] sestavené s podřízenými ovládacími prvky, které poskytují funkce vystavené nadřazeným objektem – by měly implementovat všechny vzory ovládacích prvků, které jsou obvykle přidruženy ke každému podřízenému ovládacímu prvku. Na druhé straně stejné vzory ovládacích prvků nejsou nutné implementovat podřízené ovládací prvky.  
  
<a name="uiautomation_control_pattern_includes"></a>
## <a name="ui-automation-control-pattern-components"></a>Komponenty řídicího vzoru automatizace uživatelského rozhraní  
 Vzory ovládacího prvku podporují metody, vlastnosti, události a vztahy potřebné k definování samostatné části funkce, které jsou k dispozici v ovládacím prvku.  
  
- Vztah mezi prvek automatizace uživatelského rozhraní a jeho nadřazené, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podřízené a na stejné úrovni popisuje strukturu prvku ve stromu.  
  
- Metody umožňují klientům automatizace uživatelského rozhraní manipulovat s ovládacím prvkem.  
  
- Vlastnosti a události poskytují informace o funkci vzoru ovládacího prvku, jakož i informace o stavu ovládacího prvku.  
  
 Vzory ovládacího [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvku se vztahují k objektům COM (Interface Object Model) jako rozhraní. V com, můžete dotaz objektu se zeptat, jaké rozhraní podporuje a potom použít tato rozhraní pro přístup k funkcím. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]oblasti mohou klienti automatizace uživatelského rozhraní požádat ovládací prvek, který podporuje, a potom pracovat s ovládacím prvkem prostřednictvím vlastností, metod, událostí a struktur vystavených podporovanými vzory ovládacích prvku. Například pro víceřádkové pole pro úpravy <xref:System.Windows.Automation.Provider.IScrollProvider>rozhraní implementují zprostředkovatelé automatizace uživatelského rozhraní . Když klient ví, <xref:System.Windows.Automation.AutomationElement> že <xref:System.Windows.Automation.ScrollPattern> podporuje vzor ovládacího prvku, může použít vlastnosti, metody a události vystavené tímto vzorem ovládacího prvku k manipulaci s ovládacím prvkem nebo k přístupu k informacím o ovládacím prvku.  
  
<a name="uiautomation_control_pattern_client_provider"></a>
## <a name="ui-automation-providers-and-clients"></a>Poskytovatelé a klienti automatizace uživatelského rozhraní  
 Zprostředkovatelé automatizace uživatelského rozhraní implementovat vzory ovládacího prvku vystavit vhodné chování pro konkrétní část funkce podporované ovládacího prvku.  
  
 Klienti automatizace uživatelského rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] přistupují k metodám [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]a vlastnostem [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]tříd řídicího vzoru a používají je k získání informací o rozhraní . nebo k manipulaci s . Tyto třídy vzorů ovládacího <xref:System.Windows.Automation> prvku se <xref:System.Windows.Automation.InvokePattern> nacházejí <xref:System.Windows.Automation.SelectionPattern>v oboru názvů (například a ).  
  
 Klienti <xref:System.Windows.Automation.AutomationElement> používají metody <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> (například nebo <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) nebo přístupové objekty CLR [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (COMMON Language runtime) pro přístup k vlastnostem na vzoru. Každá třída vzoru ovládacího prvku má <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>člen pole (například nebo), který identifikuje <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> tento <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> vzor ovládacího <xref:System.Windows.Automation.AutomationElement>prvku a může být předán jako parametr nebo pro načtení tohoto vzoru pro .  
  
<a name="uiautomation_control_patterns_dynamic"></a>
## <a name="dynamic-control-patterns"></a>Vzory dynamického ovládacího prvku  
 Některé ovládací prvky ne vždy podporují stejnou sadu vzorů ovládacích prvků. Vzory ovládacího prvku jsou považovány za podporované, pokud jsou k dispozici pro klienta automatizace uživatelského rozhraní. Například víceřádkové textové pole umožňuje svislé posouvání pouze v případě, že obsahuje více řádků textu, než lze zobrazit v jeho zobrazitelné oblasti. Posouvání je zakázáno, pokud je odebrán dostatek textu, takže posouvání již není nutné. V tomto příkladu scrollpattern ovládací ho diatoricky podporovánv závislosti na aktuálním stavu ovládacího prvku (kolik textu je v textovém poli).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>
## <a name="control-pattern-classes-and-interfaces"></a>Třídy vzorů a rozhraní ovládacího prvku  
 Následující tabulka popisuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvku. V tabulce jsou také uvedeny třídy používané klienty automatizace uživatelského rozhraní pro přístup ke vzorům ovládacího prvku, stejně jako rozhraní používaná poskytovateli automatizace uživatelského rozhraní k jejich implementaci.  
  
|Třída ovládacího vzoru|Rozhraní zprostředkovatele|Popis|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Používá se pro ovládací prvky, které lze ukotvit v dokovacím kontejneru. Například panely nástrojů nebo palety nástrojů.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Používá se pro ovládací prvky, které lze rozbalit nebo sbalit. Například položky nabídky v aplikaci, jako je například nabídka **Soubor.**|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Používá se pro ovládací prvky, které podporují funkce mřížky, jako je například změna velikosti a přesunutí do zadané buňky. Například zobrazení velkých ikon v Průzkumníkovi Windows nebo jednoduché tabulky bez záhlaví v aplikaci Microsoft Word.|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Používá se pro ovládací prvky, které mají buňky v mřížce. Jednotlivé buňky by měly podporovat vzor GridItem. Například každá buňka v zobrazení podrobností průzkumníka Microsoft Windows.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Používá se pro ovládací prvky, které lze vyvolat, například tlačítko.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Používá se pro ovládací prvky, které lze přepínat mezi více reprezentace stejné sady informací, dat nebo podřízených. Ovládací prvek zobrazení seznamu například o tom, kde jsou data k dispozici v zobrazení miniatur, dlaždic, ikony, seznamu nebo podrobnostech.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Používá se pro ovládací prvky, které mají rozsah hodnot, které lze použít na ovládací prvek. Například číselník ovládací prvek obsahující let může mít rozsah 1900 až 2010, zatímco jiný číselník ovládací prvek představující měsíce by měl rozsah 1 až 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Používá se pro ovládací prvky, které lze posouvat. Například ovládací prvek, který má posuvníky, které jsou aktivní, pokud je více informací, než lze zobrazit v zobrazitelné oblasti ovládacího prvku.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Používá se pro ovládací prvky, které mají jednotlivé položky v seznamu, který posouvá. Například ovládací prvek seznamu, který obsahuje jednotlivé položky v seznamu posouvání, jako je například ovládací prvek pole se seznamem.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Používá se pro ovládací prvky kontejneru výběru. Například seznamy a pole se seznamem.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Používá se pro jednotlivé položky v ovládacích prvcích kontejneru výběru, jako jsou seznamy a pole se seznamem.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Používá se pro ovládací prvky, které mají mřížku i informace záhlaví. Například listy aplikace Microsoft Excel.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Používá se pro položky v tabulce.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Používá se pro úpravy ovládacích prvků a dokumentů, které zveřejňují textové informace.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Používá se pro ovládací prvky, kde lze přepnout stav. Můžete například zaškrtnout políčka a kontrolovatelné položky nabídky.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Používá se pro ovládací prvky, které lze změnit velikost, přesunout a otočit. Typické použití pro vzor ovládacího prvku Transformace jsou v návrháři, formuláře, grafické editory a kreslicí aplikace.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Umožňuje klientům získat nebo nastavit hodnotu na ovládací prvky, které nepodporují rozsah hodnot. Například výběr času data.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Poskytuje informace specifické pro windows, základní koncept operačního systému Microsoft Windows. Příklady ovládacích prvků, které jsou windows jsou okna aplikace nejvyšší úrovně (Microsoft Word, Microsoft Windows Explorer a tak dále), více dokument rozhraní (MDI) podřízených oken a dialogových oken.|  
  
## <a name="see-also"></a>Viz také

- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
- [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md)
- [Události automatizace uživatelského rozhraní pro klienty](ui-automation-events-for-clients.md)
