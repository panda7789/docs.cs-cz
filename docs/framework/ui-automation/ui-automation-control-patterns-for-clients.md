---
title: Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 1ee0df5b133f08ec3cf6ba617c80c480e207ddf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179963"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Tento přehled zavádí vzory ovládacích informací pro klienty automatizace uživatelského rozhraní. Obsahuje informace o tom, jak může klient automatizace uživatelského [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]rozhraní použít vzory ovládacího prvku pro přístup k informacím o rozhraní .  
  
 Vzory ovládacího prvku poskytují způsob kategorizace a vystavení funkce ovládacího prvku nezávisle na typu ovládacího prvku nebo vzhledovládacího prvku. Klienti automatizace uživatelského <xref:System.Windows.Automation.AutomationElement> rozhraní můžete prozkoumat a určit, které vzory ovládacího prvku jsou podporovány a být jisti chování ovládacího prvku.  
  
 Úplný seznam vzorů ovládacích prvku naleznete [v tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>
## <a name="getting-control-patterns"></a>Získání vzorů ovládacích prvku  
 Klienti načíst vzor <xref:System.Windows.Automation.AutomationElement> ovládacího <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> prvku <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>z volání buď nebo .  
  
 Klienti mohou <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> použít metodu `IsPatternAvailable` nebo jednotlivé <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>vlastnosti (například) k určení, zda <xref:System.Windows.Automation.AutomationElement>je podporován vzorek nebo skupina vzorů na . Je však efektivnější pokusit se získat vzorek ovládacího `null` prvku a testování odkazu než zkontrolovat podporované vlastnosti a načíst vzor ovládacího prvku, protože má za následek méně volání mezi procesy.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Automation.TextPattern> získat vzor <xref:System.Windows.Automation.AutomationElement>ovládacího prvku z .  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>
## <a name="retrieving-properties-on-control-patterns"></a>Načítání vlastností u vzorů ovládacích prvku  
 Klienti mohou načíst hodnoty vlastností na <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> vzory ovládacího prvku voláním buď nebo a přetypování objektu vrácena na příslušný typ. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
 Kromě `GetPropertyValue` metod lze hodnoty vlastností načíst prostřednictvím přístupových objektů CLR (COMMON [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Language runtime) pro přístup k vlastnostem na vzoru.  
  
<a name="uiautomation_with_variable_patterns"></a>
## <a name="controls-with-variable-patterns"></a>Ovládací prvky s proměnnými vzorky  
 Některé typy ovládacích prvku podporují různé vzory v závislosti na jejich stavu nebo způsobu, jakým je ovládací prvek používán. Příklady ovládacích prvků, které mohou mít proměnná vzorky, jsou zobrazení seznamu (miniatury, dlaždice, ikony, seznam, podrobnosti), grafy aplikace Microsoft Excel (výsečový, spojnicový, pruhový, Hodnota buňky se vzorcem), oblast dokumentu aplikace Microsoft Word (Normální, Rozložení webu, Obrys, Rozložení při tisku, Tisk náhledu) a vzhledy programu Microsoft Windows Media Player.  
  
 Ovládací prvky implementující vlastní typy ovládacích prvků mohou mít libovolnou sadu vzorů ovládacích prvků, které jsou potřebné k reprezentaci jejich funkce.  
  
## <a name="see-also"></a>Viz také

- [Vzory ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns.md)
- [Vzor ovládacích prvků text pro automatizaci uživatelského rozhraní](ui-automation-text-pattern.md)
- [Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní](invoke-a-control-using-ui-automation.md)
- [Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md)
- [TextPattern Vložit text ukázkový text](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Ukázka hledání a výběru textových vzorů](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [InvokePattern, ExpandCollapsePattern a TogglePattern Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
