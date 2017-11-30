---
title: "Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1d556b3da13b70a0a5e69eb72905e04a01dffa9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled zavádí vzory ovládacích prvků pro klienty automatizace uživatelského rozhraní. Obsahuje informace o tom, jak můžete použít vzory ovládacích prvků pro přístup k informacím o automatizace uživatelského rozhraní klienta [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Vzory ovládacích prvků umožňují zařadit do kategorií a vystavit funkcionalitu ovládacího prvku nezávislé na typ ovládacího prvku nebo vzhledu ovládacího prvku. Klienti automatizace uživatelského rozhraní můžete zkontrolovat <xref:System.Windows.Automation.AutomationElement> a určit, který ovládací prvek vzory jsou podporovány být jistí, chování ovládacího prvku.  
  
 Úplný seznam vzorů ovládacích prvků, najdete v části [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Načítání vzorů ovládacích prvků  
 Klienti získat vzor ovládacích prvků z <xref:System.Windows.Automation.AutomationElement> voláním buď <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Klienti mohou používat <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> metoda nebo jednotlivce `IsPatternAvailable` vlastnosti (například <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) k určení, jestli je na podporovaný vzor nebo skupinu schémat <xref:System.Windows.Automation.AutomationElement>. Je však efektivnější pokoušet o získání vzor ovládacích prvků a otestovat `null` odkaz, než se kontrola podporovaných vlastností a načíst vzor ovládacích prvků, protože výsledkem je to méně volání mezi procesy.  
  
 Následující příklad ukazuje, jak získat <xref:System.Windows.Automation.TextPattern> – vzor ovládacích prvků z <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Načítání vlastností na vzory ovládacích prvků  
 Klienti mohou získat hodnoty vlastností na vzory ovládacích prvků voláním buď <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> a přetypování objekt vrácen do příslušného typu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
 Kromě `GetPropertyValue` metody, hodnoty vlastností se dají získat pomocí [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] přístupových objektů pro přístup k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti vzor.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Ovládací prvky s proměnné vzory  
 Některé typy ovládacích prvků podporují různé vzorce v závislosti na jejich stavu nebo způsobem, ve kterém je používán ovládacího prvku. Příklady ovládacích prvků, které může mít proměnné vzory se zobrazení seznamu (miniatur, dlaždice, ikony, seznam, podrobnosti), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafy (Pie, řádku, řádku a buňky hodnotu s vzorec), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]na oblasti (normální rozložení webové stránky Outline, rozložení tisku tisk dokumentů Ve verzi Preview) a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] vzhledy.  
  
 Ovládací prvky, které implementují typy vlastní ovládací prvek může mít libovolnou sadu vzorů ovládacích prvků, které jsou potřebné k reprezentaci jejich funkce.  
  
## <a name="see-also"></a>Viz také  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)  
 [Vzoru prvků Text pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)  
 [Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Ukázka TextPattern vložení textu](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [TextPattern vyhledávání a výběru vzorku](http://msdn.microsoft.com/en-us/0a3bca57-8b72-489d-a57c-da85b7a22c7f)  
 [Vlastnost InvokePattern a ukázkové položky nabídky ExpandCollapsePattern](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
