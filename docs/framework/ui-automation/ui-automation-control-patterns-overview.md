---
title: Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: a3daf75417260d7e761da2e90c595471b2a4b2a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131517"
---
# <a name="ui-automation-control-patterns-overview"></a>Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled zavádí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vzorů ovládacích prvků. Vzory ovládacích prvků poskytují způsob kategorizace a vystavení funkcí ovládacího prvku nezávisle na typu ovládacího prvku nebo vzhledu ovládacího prvku.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] používá vzory ovládacích prvků pro reprezentaci obecného chování ovládacího prvku. Například můžete použít vzor ovládacího prvku Invoke pro ovládací prvky, které mohou být vyvolány (například tlačítka) a řídicí vzor posuvníku pro ovládací prvky, které mají posuvníky (například seznamy, zobrazení seznamu nebo pole se seznamem). Vzhledem k tomu, že každý vzor ovládacích prvků představuje samostatné funkce, lze je kombinovat a popsat tak úplnou sadu funkcí podporovaných určitým ovládacím prvkem.  
  
> [!NOTE]
> Agregační ovládací prvky – sestavené s podřízenými ovládacími prvky, které poskytují [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] pro funkce vystavené nadřazeným prvkem, by měly implementovat všechny vzory ovládacích prvků, které jsou obvykle spojeny s každým podřízeným V takovém případě tyto stejné vzory ovládacích prvků není nutné implementovat podřízenými ovládacími prvky.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>Komponenty vzoru ovládacího prvku automatizace uživatelského rozhraní  
 Vzory ovládacích prvků podporují metody, vlastnosti, události a relace potřebné k definování diskrétního prvku, který je k dispozici v ovládacím prvku.  
  
- Vztah mezi prvkem automatizace uživatelského rozhraní a jeho nadřazeným objektem, podřízenými prvky a členy na stejné úrovni popisuje strukturu elementu v rámci stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
- Metody umožňují klientům automatizace uživatelského rozhraní manipulovat s ovládacím prvkem.  
  
- Vlastnosti a události poskytují informace o funkci vzoru ovládacího prvku a také informace o stavu ovládacího prvku.  
  
 Vzory ovládacích prvků se vztahují na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jako rozhraní vztahující se k objektům modelu COM (Component Object Model). V modelu COM můžete zadat dotaz na objekt, který požaduje, jaká rozhraní podporuje, a pak použít tato rozhraní k přístupu k funkcím. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]můžou klienti automatizace uživatelského rozhraní požádat o ovládací prvek, který řídicí modely podporuje, a pak s ovládacím prvkem pracovat prostřednictvím vlastností, metod, událostí a struktur zveřejněných pomocí podporovaných vzorů ovládacích prvků. Například pro víceřádkové textové pole Zprostředkovatelé automatizace uživatelského rozhraní implementují <xref:System.Windows.Automation.Provider.IScrollProvider>. Když klient ví, že <xref:System.Windows.Automation.AutomationElement> podporuje vzor ovládacího prvku <xref:System.Windows.Automation.ScrollPattern>, může použít vlastnosti, metody a události vystavené tímto vzorovým ovládacím prvkem pro manipulaci s ovládacím prvkem nebo přístup k informacím o ovládacím prvku.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>Zprostředkovatelé automatizace uživatelského rozhraní a klienti  
 Zprostředkovatelé automatizace uživatelského rozhraní implementují vzory ovládacích prvků, které vystavují vhodné chování pro konkrétní druh funkcí podporovaných ovládacím prvkem.  
  
 Klienti automatizace uživatelského rozhraní přistupují k metodám a vlastnostem tříd vzorů ovládacích prvků [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a používají je k získání informací o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]nebo k manipulaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Tyto třídy vzorů ovládacích prvků jsou nalezeny v oboru názvů <xref:System.Windows.Automation> (například <xref:System.Windows.Automation.InvokePattern> a <xref:System.Windows.Automation.SelectionPattern>).  
  
 Klienti používají metody <xref:System.Windows.Automation.AutomationElement> (například <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) nebo přistupující objekty modulu CLR (Common Language Runtime) k přístupu k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]m vlastnostem vzoru. Každá třída vzoru ovládacího prvku má člen pole (například <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>), který identifikuje vzor ovládacího prvku a může být předán jako parametr pro <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> k načtení tohoto vzoru pro <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Vzory dynamických ovládacích prvků  
 Některé ovládací prvky vždy nepodporují stejnou sadu vzorů ovládacích prvků. Vzory ovládacích prvků jsou považovány za podporované, pokud jsou k dispozici pro klienta automatizace uživatelského rozhraní. Například víceřádkové textové pole umožňuje svislé posouvání pouze v případě, že obsahuje více řádků textu, než může být zobrazeno v zobrazitelné oblasti. Posouvání je vypnuto, pokud je odebráno dostatečné množství textu, takže posouvání již není vyžadováno. V tomto příkladu je vzor ovládacího prvku ScrollPattern dynamicky podporován v závislosti na aktuálním stavu ovládacího prvku (kolik textu je v poli pro úpravy).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Třídy a rozhraní vzoru ovládacích prvků  
 Následující tabulka popisuje vzory ovládacích prvků [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Tabulka také uvádí seznam tříd používaných klienty automatizace uživatelského rozhraní pro přístup k vzorům ovládacích prvků a k implementaci rozhraní používaných zprostředkovateli automatizace uživatelského rozhraní.  
  
|Třída vzoru ovládacího prvku|Rozhraní poskytovatele|Popis|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Používá se pro ovládací prvky, které mohou být ukotveny v Dock kontejneru. Například panely nástrojů nebo palety nástrojů.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Používá se pro ovládací prvky, které se dají rozbalit nebo sbalit. Například položky nabídky v aplikaci, jako je například nabídka **soubor** .|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Používá se pro ovládací prvky, které podporují funkce mřížky, jako je třeba určení velikosti a přesun do zadané buňky. Například zobrazení velkých ikon v Průzkumníkovi Windows nebo jednoduchých tabulkách bez hlaviček v [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Používá se pro ovládací prvky, které obsahují buňky v Gridech. Jednotlivé buňky by měly podporovat vzor GridItem. Například každá buňka v Průzkumníkovi Windows má podrobné zobrazení.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Používá se pro ovládací prvky, které mohou být vyvolány, například tlačítko.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Používá se pro ovládací prvky, které mohou přepínat mezi různými reprezentacemi stejné sady informací, dat nebo podřízených objektů. Například ovládací prvek zobrazení seznamu, kde jsou data k dispozici v zobrazení Miniatura, dlaždice, ikona, seznam nebo zobrazení podrobností.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Používá se pro ovládací prvky, které mají rozsah hodnot, které lze použít pro ovládací prvek. Například číselníkový ovládací prvek obsahující roky může mít rozmezí 1900 až 2010, zatímco další číselník, který prezentuje měsíce, by měl být v rozsahu od 1 do 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Používá se pro ovládací prvky, které se můžou posouvat. Například ovládací prvek, který má aktivní posuvníky, pokud existuje více informací, než lze zobrazit v zobrazitelné oblasti ovládacího prvku.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Používá se pro ovládací prvky, které mají jednotlivé položky v seznamu, který se posouvá. Například ovládací prvek seznamu, který má jednotlivé položky v rolovacím seznamu, jako je například ovládací prvek pole se seznamem.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Používá se pro ovládací prvky kontejneru výběru. Například seznam polí a polí se seznamem.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Používá se pro jednotlivé položky v ovládacích prvcích kontejneru výběru, jako jsou seznamy a pole se seznamem.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Používá se pro ovládací prvky, které mají tabulku a informace záhlaví. Například [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] listy.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Používá se pro položky v tabulce.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Používá se pro úpravy ovládacích prvků a dokumentů, které zpřístupňují textové informace.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Používá se pro ovládací prvky, kde lze stav přepínat. Například zaškrtávací políčka a položky nabídky, které se mají kontrolovat.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Používá se pro ovládací prvky, které se dají změnit na velikost, přesunout a otočit. Typická použití pro vzor ovládacích prvků transformace jsou návrháři, formuláře, grafické editory a aplikace pro kreslení.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Umožňuje klientům získat nebo nastavit hodnotu u ovládacích prvků, které nepodporují rozsah hodnot. Například výběr data a času.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Zpřístupňuje informace specifické pro systém Windows, což je základní koncept operačního systému Microsoft Windows. Příklady ovládacích prvků, které jsou Windows, jsou okna aplikace nejvyšší úrovně ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], Průzkumník Microsoft Windows atd.), podřízené okna rozhraní MDI (Multiple Document Interface) a dialogová okna.|  
  
## <a name="see-also"></a>Viz také:

- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
- [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md)
- [Události automatizace uživatelského rozhraní pro klienty](ui-automation-events-for-clients.md)
