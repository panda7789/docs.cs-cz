---
title: Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 82415524e60a1c9cf44cdccd9a1b2660f4b517a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607732"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled zavádí vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní. Obsahuje informace o automatizaci uživatelského rozhraní klienta použití vzorů ovládacích prvků pro přístup k informacím o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Vzory ovládacích prvků umožňují zařadit do kategorií a ovládací prvek funkci nezávisle na typ ovládacího prvku nebo vzhled ovládacího prvku. Klienti automatizace uživatelského rozhraní můžete prozkoumat <xref:System.Windows.Automation.AutomationElement> rozhodnout, který ovládací prvek vzorce jsou podporovány lze a chování ovládacího prvku.  
  
 Úplný seznam vzorů ovládacích prvků, naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Načítání vzorů ovládacích prvků  
 Klienti získat vzor ovládacích prvků ze <xref:System.Windows.Automation.AutomationElement> voláním buď <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Klienti mohou používat <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> metoda nebo jednotlivce `IsPatternAvailable` vlastnosti (například <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) Chcete-li zjistit, jestli je na podporuje model nebo skupiny vzory <xref:System.Windows.Automation.AutomationElement>. Je však mnohem efektivnější, pokusí se získat vzor ovládacích prvků a test pro `null` odkaz než zkontrolujte podporovaných vlastností a načíst vzor ovládacích prvků, protože to má za následek méně mezi procesní volání.  
  
 Následující příklad ukazuje, jak získat <xref:System.Windows.Automation.TextPattern> – vzor ovládacích prvků ze <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Načítání vlastností na vzorů ovládacích prvků  
 Klienti mohou získat hodnoty vlastností v vzorů ovládacích prvků pomocí volání buď <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> a přetypování objekt vrácen do příslušného typu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
 Kromě `GetPropertyValue` metody, hodnoty vlastností se dají získat pomocí [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] přístupové objekty pro přístup k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostem vzorce.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Ovládací prvky s variabilní vzorky  
 Některé typy ovládacích prvků podporují různé vzorce v závislosti na jejich stav nebo způsobem, který je používán ovládací prvek. Příklady ovládacích prvků, které mají variabilní vzorky jsou seznamy (miniatury, dlaždice, ikony, seznam, podrobnosti), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafy (Pie, řádek panelu hodnotu buňky pomocí vzorce), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]vaší oblasti (normální, rozložení webové stránky, osnovy, rozložení při tisku, tisk dokumentů Ve verzi Preview), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skinů v šablonách.  
  
 Ovládací prvky, které implementují typy vlastní ovládací prvek může mít libovolnou sadu vzorů ovládacích prvků, které jsou potřeba k reprezentaci jejich funkce.  
  
## <a name="see-also"></a>Viz také:
- [Vzory ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)
- [Vzor ovládacích prvků text pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)
- [Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)
- [Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [Ukázka vložení prvku TextPattern textu](https://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
- [TextPattern vyhledávání a výběr ukázky](https://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)
- [Vlastnost InvokePattern a ukázkové položky nabídky ExpandCollapsePattern](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
