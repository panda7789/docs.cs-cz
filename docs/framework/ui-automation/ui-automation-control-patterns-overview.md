---
title: Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: fc07cc23498b2079aba41dfa57c26b88944d6a8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033082"
---
# <a name="ui-automation-control-patterns-overview"></a>Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled zavádí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] řídit vzory. Vzory ovládacích prvků umožňují zařadit do kategorií a ovládací prvek funkci nezávisle na typ ovládacího prvku nebo vzhled ovládacího prvku.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] použití řízení vzory představují společné chování ovládacího prvku. Například použijte vzor ovládacích prvků Invoke pro ovládací prvky, které může být vyvolána (například tlačítka) a vzoru ovládacích prvků posuv pro ovládací prvky, které mají posuvníky (například seznamy, seznamy nebo pole se seznamem). Protože každý – vzor ovládacích prvků představuje samostatnou funkci, mohou být kombinovány pro popis úplnou sadu funkcí podporovaných jazykem konkrétní ovládací prvek.  
  
> [!NOTE]
>  Agregovat ovládací prvky – vytvořených pomocí podřízených ovládacích prvků, které poskytují [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] pro funkce vystavené nadřazenou položkou – by měly implementovat všechny vzorů ovládacích prvků, které jsou obvykle spojené s každou podřízený ovládací prvek. Pak tyto stejné vzorů ovládacích prvků se nevyžadují pro implementaci v podřízených ovládacích prvků.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>Součásti vzor ovládacího prvku automatizace uživatelského rozhraní  
 Vzory ovládacích prvků podporují metody, vlastnosti, události a vztahy, které jsou potřebné k definování samostatná část funkce je dostupná v ovládacím prvku.  
  
- Vztah mezi prvku automatizace uživatelského rozhraní a jeho nadřazeného, podřízené položky a na stejné úrovni popisuje strukturu prvku v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.  
  
- Metody klientům automatizace uživatelského rozhraní pro manipulaci s ovládacího prvku.  
  
- Vlastnosti a události poskytují informace o funkcích vzor ovládacích prvků a informace o stavu ovládacího prvku.  
  
 Vzory ovládacích prvků se týkají [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] rozhraní vztah k [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] objekty. V [!INCLUDE[TLA2#tla_com](../../../includes/tla2sharptla-com-md.md)], můžete dát dotaz na objekt požádejte ji co rozhraní podporuje, a pak pomocí těchto rozhraní pro přístup k funkcím. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], klienti automatizace uživatelského rozhraní požádejte ovládací prvek, který vzorů ovládacích prvků se podporuje a pak pracovat s ovládacím prvkem vlastnosti, metody, události a struktury vystavené vzory podporovaných ovládacích prvků. Například pro pole víceřádková textová pole, implementace zprostředkovatelů automatizace uživatelského rozhraní <xref:System.Windows.Automation.Provider.IScrollProvider>. Když klient ví, <xref:System.Windows.Automation.AutomationElement> podporuje <xref:System.Windows.Automation.ScrollPattern> – vzor ovládacích prvků, může použít vlastnosti, metody a události, které jsou vystavené této – vzor ovládacích prvků k manipulovat s prvkem nebo přístup k informacím o ovládacím prvku.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>Zprostředkovatelé automatizace uživatelského rozhraní a klientů  
 Implementace zprostředkovatelů automatizace uživatelského rozhraní vzorů ovládacích prvků k vystavení odpovídající chování pro určitou část funkcí podporovaných jazykem ovládacího prvku.  
  
 Klienti automatizace uživatelského rozhraní přístup k metodám a vlastnostem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzor třídy a využít k získání informací [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], nebo k manipulaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Tyto třídy vzor ovládacích prvků se nacházejí v <xref:System.Windows.Automation> obor názvů (například <xref:System.Windows.Automation.InvokePattern> a <xref:System.Windows.Automation.SelectionPattern>).  
  
 Klienti používají <xref:System.Windows.Automation.AutomationElement> metod (například <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) nebo [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] přístupové objekty pro přístup k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostem vzorce. Každá třída vzor ovládací prvek má člena pole (například <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>), který identifikuje tento – vzor ovládacích prvků a mohou být předány jako parametr <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> načíst tento vzor pro <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Vzory dynamických ovládacích prvků  
 Některé ovládací prvky vždy stejnou sadu vzorů ovládacích prvků nepodporují. Vzory ovládacích prvků jsou považovány za podporovány, pokud jsou k dispozici pro automatizaci uživatelského rozhraní klienta. Můžete třeba upravit Víceřádkový umožňuje svislé posouvání, pouze pokud obsahuje více řádků textu, než lze zobrazit ve své oblasti zobrazit. Posouvání je zakázáno, pokud je dostatek text odebrat tak, aby posouvání se už nevyžaduje. V tomto příkladu vlastnost ScrollPattern – vzor ovládacích prvků se podporuje dynamicky v závislosti na aktuální stav ovládacího prvku (kolik text je do textového pole).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Třídy ovládacích prvků modelu a rozhraní  
 V následující tabulce jsou popsány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory. V tabulce jsou uvedeny také třídy používané klienty automatizace uživatelského rozhraní pro přístup k vzorů ovládacích prvků, jakož i rozhraní používaných zprostředkovatelů automatizace uživatelského rozhraní pro jejich implementaci.  
  
|Třída vzor ovládacích prvků|Rozhraní zprostředkovatele|Popis|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Používá se pro ovládací prvky, které lze ukotvit v kontejneru ukotvení. Například panely nástrojů nebo nástroj palety.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Používá se pro ovládací prvky, které můžete rozbalit nebo sbalit. Například nabídka položek v aplikaci, jako **souboru** nabídky.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Používá se pro ovládací prvky, které podporují funkce mřížky, jako je například změna velikosti a přesunutí do zadaná buňka. Například zobrazit velké ikony v Průzkumníku Windows nebo jednoduché tabulky bez záhlaví v [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Používá se pro ovládací prvky, které mají buněk v rámci mřížky. Položka GridItem vzor by měly podporovat jednotlivých buněk. Například každá buňka [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] podrobností zobrazení.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Používá se pro ovládací prvky, které mohou být vyvolány, jako je například tlačítko.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Používá se pro ovládací prvky, které můžete přepínat mezi více reprezentací stejnou sadu informace, dat nebo podřízené položky. Zobrazení seznamu například řídit, kdy data jsou k dispozici v miniaturu, dlaždice, ikony, seznamu nebo zobrazení podrobností.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Používá se pro ovládací prvky, které mají rozsah hodnot, které lze použít u ovládacího prvku. Například číselník obsahující let může mají celou řadu 1900 až 2010 jiného ovládacího prvku číselník nabízí ten samý měsíců by mají celou řadu 1 až 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Používá se pro ovládací prvky, které můžete posouvat. Například ovládací prvek, který obsahuje posuvníky, které jsou aktivní, když nejsou k dispozici další informace, než lze zobrazit v oblasti zobrazit ovládacího prvku.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Používá se pro ovládací prvky, které se mají jednotlivé položky v seznamu, umožňuje posouvání. Například ovládací prvek seznamu, který obsahuje jednotlivé položky v seznamu posuvníku, jako je například ovládací prvek pole se seznamem.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Používá se pro ovládací prvky výběru kontejneru. Například seznamy a pole se seznamem.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Použít u jednotlivých položek v ovládacích prvcích kontejneru výběru, jako je například seznamy a pole se seznamem.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Použít pro ovládací prvky, které mají mřížky a také informace záhlaví. Například [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] listů.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Použitá pro položky v tabulce.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Používá pro ovládacích prvcích pro úpravy a dokumenty, které zpřístupňují textové informace.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Použít pro ovládací prvky, kde lze přepínat stav. Například zaškrtněte políčka a položky kontrolovatelné nabídky.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Používá se pro ovládací prvky, které můžete se změněnou velikostí, přesouvat a otočen. Obvyklá využití pro vzoru ovládacích prvků transformace jsou v návrháři, formulářů, grafické editory a výkresu aplikace.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Umožňuje klientům získat nebo nastavit hodnotu na ovládací prvky, které nepodporují rozsah hodnot. Například výběr data a času.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Poskytuje informace specifické pro systém windows, základní koncept pro [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] operačního systému. Příklady ovládacích prvků, které jsou okna nejvyšší úrovně aplikace pro windows ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], a tak dále), [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] podřízená okna a dialogová okna.|  
  
## <a name="see-also"></a>Viz také:

- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
- [Vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [Události automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
