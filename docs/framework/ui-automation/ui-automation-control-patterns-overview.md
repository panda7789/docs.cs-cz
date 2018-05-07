---
title: Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1b02618676a1162681c67d34a2c6f43def07893c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-control-patterns-overview"></a>Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled zavádí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] řízení vzory. Vzory ovládacích prvků umožňují zařadit do kategorií a vystavit funkcionalitu ovládacího prvku nezávislé na typ ovládacího prvku nebo vzhledu ovládacího prvku.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] používá řízení vzory představují společné chování ovládacího prvku. Například použít vzor Invoke ovládacích prvků pro ovládací prvky, které mohou být vyvolány (např. tlačítka) a vzoru ovládacích prvků posuv pro ovládací prvky, které mají posuvníky (například seznamy, seznamy nebo pole se seznamem). Protože každý – vzor ovládacích prvků představuje samostatnou funkci, mohou být kombinovány k popisu úplnou sadu funkcí konkrétní ovládacím prvkem podporována.  
  
> [!NOTE]
>  Agregace ovládací prvky – vytvořené s nástroji podřízených ovládacích prvků, které poskytují [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] pro funkce vystavené nadřízený objekt – měli implementovat všechny vzory ovládacích prvků obvykle spojené s každou podřízený ovládací prvek. Tyto stejné vzory ovládacích prvků zase, nejsou nutné k implementaci pomocí podřízených ovládacích prvků.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>Součásti vzor ovládacího prvku automatizace uživatelského rozhraní  
 Vzory ovládacích prvků podporovat metody, vlastnosti, události a vztahy, které jsou potřebné k definování samostatná část funkce je k dispozici v ovládacím prvku.  
  
-   Vztah mezi prvku automatizace uživatelského rozhraní a jeho nadřazené, děti a na stejné úrovni popisuje strukturu elementu v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.  
  
-   Metody klientům automatizace uživatelského rozhraní k manipulaci s ovládacího prvku.  
  
-   Vlastnosti a události poskytují informace o funkcích vzor ovládacích prvků, a také informace o stavu ovládacího prvku.  
  
 Vzory ovládacích prvků, na které se týkají [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jako rozhraní se týkají [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] objekty. V [!INCLUDE[TLA2#tla_com](../../../includes/tla2sharptla-com-md.md)], můžete dát dotaz na objekt, požádejte ho co rozhraní podporuje, a potom pomocí těchto rozhraní, které se funkce přístupu. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], klienti automatizace uživatelského rozhraní můžete požádat ovládacího prvku, který vzorů ovládacích prvků ji podporuje a poté musí komunikovat pomocí ovládacího prvku prostřednictvím vlastnosti, metody, události a struktury vystavené vzory podporované ovládacích prvků. Například pro víceřádkový textové pole, zprostředkovatelé automatizace uživatelského rozhraní implementují <xref:System.Windows.Automation.Provider.IScrollProvider>. Když klient zná, který <xref:System.Windows.Automation.AutomationElement> podporuje <xref:System.Windows.Automation.ScrollPattern> – vzor ovládacích prvků, může použít vlastnosti, metod a události, které jsou zveřejněné podle tohoto vzoru ovládacích prvků k ovládání ovládací prvek nebo přístup k informacím o ovládacího prvku.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>Zprostředkovatelé automatizace uživatelského rozhraní a klienty  
 Zprostředkovatelé automatizace uživatelského rozhraní implementují vzory ovládacích prvků tak, aby se zveřejnily odpovídající chování pro konkrétní funkce ovládacím prvkem podporována.  
  
 Klienti automatizace uživatelského rozhraní přístup metody a vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzor třídy a použít je k získání informací [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], nebo k manipulaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Tyto třídy vzor ovládacích prvků, které se nacházejí v <xref:System.Windows.Automation> obor názvů (například <xref:System.Windows.Automation.InvokePattern> a <xref:System.Windows.Automation.SelectionPattern>).  
  
 Klienti používají <xref:System.Windows.Automation.AutomationElement> metody (například <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) nebo [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] přístupových objektů pro přístup k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti se vzorem. Každá třída vzor řízení má členem pole (například <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType>'' nebo <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>), identifikuje tento vzor ovládacích prvků a může být předána jako parametr, který se <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> načíst tento vzor <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Vzory dynamických ovládacích prvků  
 Některé ovládací prvky vždy stejnou sadu vzorů ovládacích prvků nepodporují. Vzory ovládacích prvků, jsou považovány za podporovány, pokud jsou k dispozici pro automatizaci uživatelského rozhraní klienta. Například víceřádkového upravit umožňuje svislé posouvání jenom v případě, že obsahuje více řádků textu, než lze zobrazit v jeho zobrazitelné oblasti. Posouvání je zakázána, když dojde k odebrání dostatek text tak, aby posouvání se už nevyžaduje. V tomto příkladu je vzor vlastnost ScrollPattern ovládacích prvků dynamicky podporována v závislosti na aktuální stav ovládacího prvku (množství textu je do textového pole).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Ovládací prvek vzor třídy a rozhraní  
 V následující tabulce jsou popsány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory. Tabulka také uvádí třídy používané klienty automatizace uživatelského rozhraní pro přístup k vzory ovládacích prvků, jakož i rozhraní používaných zprostředkovateli automatizace uživatelského rozhraní pro jejich implementaci.  
  
|Třída vzor ovládacích prvků|Zprostředkovatel rozhraní|Popis|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Použít pro ovládací prvky, které lze ukotvit v ukotvení kontejneru. Například panely nástrojů nebo palety nástroj.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Použít pro ovládací prvky, které můžete rozbalit nebo sbalit. Například nabídky položek v aplikaci, jako **souboru** nabídky.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Použít pro ovládací prvky, které podporují funkce mřížky, jako je změna velikosti a přesunutí zadaná buňka. Například velké ikony zobrazit v Průzkumníku Windows nebo jednoduchý tabulky bez hlavičky v [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Použít pro ovládací prvky, které mají buněk v rámci mřížky. GridItem – vzor by měly podporovat jednotlivých buněk. Například každá buňka [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] podrobností zobrazení.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Použít pro ovládací prvky, které mohou být vyvolány, jako je tlačítko.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Použít pro ovládací prvky, které můžete přepínat mezi více reprezentace stejnou sadu informace, data nebo podřízené objekty. Zobrazení seznamu například řídit, kde je k dispozici v miniaturu, dlaždice, ikona, seznamu nebo zobrazení podrobností data.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Použít pro ovládací prvky, které mají rozsah hodnot, které mohou být použity k ovládacímu prvku. Ovládacího prvku číselník obsahující let například může mít řadu 1900 až 2010, zatímco jiné číselník prezentací měsíců by mít rozsah 1 až 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Použít pro ovládací prvky, které lze posunout. Například ovládací prvek, obsahuje posuvníky, které jsou aktivní, pokud obsahuje další informace, než lze zobrazit v oblasti zobrazitelné ovládacího prvku.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Použít pro ovládací prvky, které jsou jednotlivé položky v seznamu, který se posouvá společně. Například ovládací prvek seznamu, který má jednotlivé položky v seznamu přejděte například ovládacího prvku pole se seznamem.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Použít pro ovládací prvky pro výběr kontejneru. Například seznamy a pole se seznamem.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Použít pro jednotlivé položky v ovládacích prvcích kontejneru výběr, jako je například seznamy a pole se seznamem.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Použít pro ovládací prvky, které mají mřížka a také informace hlavičky. Například [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] listů.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Použít pro položky v tabulce.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Použít pro ovládacích prvcích pro úpravy a dokumenty, které zveřejňují textové informace.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Použít pro ovládací prvky, kde stavu můžou být. Například zaškrtněte políčka a položky kontrolovatelné nabídky.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Použít pro ovládací prvky, které je možné po změně velikosti, přesunout a otočen. Typické použití vzoru ovládacích prvků transformace jsou v návrháři, formulářů, grafické editory a kreslení aplikace.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Umožňuje klientům získat nebo nastavit hodnotu na ovládací prvky, které nepodporují rozsah hodnot. Například výběr data a času.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Zveřejňuje informace o specifických pro systém windows, základní koncept jako [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] operačního systému. Příklady ovládacích prvků, které jsou windows jsou nejvyšší úrovně aplikace windows ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)]a tak dále), [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] podřízená okna a dialogová okna.|  
  
## <a name="see-also"></a>Viz také  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [Vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [Události automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
