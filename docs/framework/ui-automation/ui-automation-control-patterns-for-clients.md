---
title: Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 193049aed6da3375b687e465678dca4dc90e6b39
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448809"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Tento přehled představuje vzory ovládacích prvků pro klienty automatizace uživatelského rozhraní. Obsahuje informace o tom, jak může klient automatizace uživatelského rozhraní používat vzory ovládacích prvků pro přístup k informacím o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Vzory ovládacích prvků poskytují způsob kategorizace a vystavení funkcí ovládacího prvku nezávisle na typu ovládacího prvku nebo vzhledu ovládacího prvku. Klienti automatizace uživatelského rozhraní mohou prozkoumávat <xref:System.Windows.Automation.AutomationElement> a určit, které modely ovládacích prvků jsou podporovány a které mají být zaručeny chování ovládacího prvku.  
  
 Úplný seznam vzorů ovládacích prvků najdete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Načítání vzorů ovládacích prvků  
 Klienti načtou vzor ovládacího prvku z <xref:System.Windows.Automation.AutomationElement> voláním <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Klienti mohou použít metodu <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> nebo individuální vlastnost `IsPatternAvailable` (například <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) k určení, zda je v <xref:System.Windows.Automation.AutomationElement>podporován vzor nebo skupina vzorů. Je však efektivnější pokus o získání vzoru ovládacího prvku a testování `null` odkazování, než ke kontrole podporovaných vlastností a načtení vzoru ovládacího prvku, protože to vede k menšímu počtu volání mezi procesy.  
  
 Následující příklad ukazuje, jak získat <xref:System.Windows.Automation.TextPattern> vzor ovládacího prvku z <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Načítání vlastností pro vzory ovládacích prvků  
 Klienti mohou načíst hodnoty vlastností pro vzory ovládacích prvků voláním <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> a přetypování objektu vráceného na příslušný typ. Další informace o vlastnostech [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
 Kromě metod `GetPropertyValue` lze hodnoty vlastností načíst prostřednictvím přístupových objektů modulu CLR (Common Language Runtime) pro přístup k vlastnostem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve vzoru.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Ovládací prvky se vzory proměnných  
 Některé typy ovládacích prvků podporují různé vzory v závislosti na jejich stavu nebo způsobu, jakým je ovládací prvek používán. Příklady ovládacích prvků, které mohou mít variabilní vzorce, jsou zobrazení seznamu (miniatury, dlaždice, ikony, seznam, podrobnosti), grafy aplikace Microsoft Excel (výsečový, řádek, pruh, hodnota buňky se vzorcem), oblast dokumentu aplikace Microsoft Word (normální, webové rozložení, osnova, rozložení tisku, tisk Preview) a Microsoft Windows Media Player skiny.  
  
 Ovládací prvky implementující vlastní typy ovládacích prvků mohou mít libovolnou sadu vzorů ovládacích prvků, které jsou nutné pro reprezentaci jejich funkcí.  
  
## <a name="see-also"></a>Viz také:

- [Vzory ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns.md)
- [Vzor ovládacích prvků text pro automatizaci uživatelského rozhraní](ui-automation-text-pattern.md)
- [Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní](invoke-a-control-using-ui-automation.md)
- [Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md)
- [Ukázka vložení textu TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Ukázka hledání a výběru TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [Ukázka InvokePattern, ExpandCollapsePattern a TogglePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
