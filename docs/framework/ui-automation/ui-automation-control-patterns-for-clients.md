---
title: Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 320833bf147fa16889cd188c7c729cd4dc028843
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042525"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Tento přehled představuje vzory ovládacích prvků pro klienty automatizace uživatelského rozhraní. Obsahuje informace o tom, jak může klient automatizace uživatelského rozhraní použít vzory ovládacích prvků pro přístup k [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]informacím o.  
  
 Vzory ovládacích prvků poskytují způsob kategorizace a vystavení funkcí ovládacího prvku nezávisle na typu ovládacího prvku nebo vzhledu ovládacího prvku. Klienti automatizace uživatelského rozhraní mohou prošetřit <xref:System.Windows.Automation.AutomationElement> a zjistit, které modely ovládacích prvků jsou podporovány a které mají být zaručeny chování ovládacího prvku.  
  
 Úplný seznam vzorů ovládacích prvků najdete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Načítání vzorů ovládacích prvků  
 Klienti načítají řídicí vzor <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> voláním nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Klienti mohou použít <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> metodu nebo <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>individuální `IsPatternAvailable` vlastnost (například) k určení, zda je v prvku podporován vzor <xref:System.Windows.Automation.AutomationElement>nebo skupina vzorů. Je však efektivnější pokus o získání vzoru ovládacího prvku a testu pro `null` referenci než pro kontrolu podporovaných vlastností a načtení vzoru ovládacího prvku, protože výsledkem je menší počet volání mezi procesy.  
  
 Následující příklad ukazuje, jak získat <xref:System.Windows.Automation.TextPattern> vzor ovládacího prvku <xref:System.Windows.Automation.AutomationElement>z.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Načítání vlastností pro vzory ovládacích prvků  
 Klienti mohou načíst hodnoty vlastností u vzorů ovládacích prvků voláním <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> a přetypováním objektu vráceného do příslušného typu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
 Kromě `GetPropertyValue` metod lze hodnoty vlastností načíst prostřednictvím přístupových objektů modulu CLR (Common Language Runtime) pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] přístup k vlastnostem vzoru.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Ovládací prvky se vzory proměnných  
 Některé typy ovládacích prvků podporují různé vzory v závislosti na jejich stavu nebo způsobu, jakým je ovládací prvek používán. Příklady ovládacích prvků, které mohou mít proměnlivé vzorce, jsou zobrazení seznamu (miniatury, dlaždice, ikony, seznam [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] , podrobnosti), grafy (výsečové, Spojnicová, pruhová, hodnota [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]buňky se vzorcem), oblast dokumentu (normální, rozložení na webu, osnova, rozložení tisku, tisk Preview) a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] vzhledy.  
  
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
