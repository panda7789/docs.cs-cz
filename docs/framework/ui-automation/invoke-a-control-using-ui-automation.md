---
title: Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: e1b489e8daaaf9f5b8c0cb46374fa54bf165d49c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447012"
---
# <a name="invoke-a-control-using-ui-automation"></a>Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma ukazuje, jak provádět následující úlohy:  
  
- Vyhledání ovládacího prvku, který odpovídá podmínkám konkrétní vlastnosti, procházením zobrazení ovládacího prvku stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pro cílovou aplikaci.  
  
- Vytvořte <xref:System.Windows.Automation.AutomationElement> pro každý ovládací prvek.  
  
- Získejte <xref:System.Windows.Automation.InvokePattern> objekt z jakéhokoli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu, který podporuje vzor ovládacího prvku <xref:System.Windows.Automation.InvokePattern>.  
  
- Použijte <xref:System.Windows.Automation.InvokePattern.Invoke%2A> k vyvolání ovládacího prvku z klientské obslužné rutiny události.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá metodu <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> třídy <xref:System.Windows.Automation.AutomationElement> ke generování objektu <xref:System.Windows.Automation.InvokePattern> a k vyvolání ovládacího prvku pomocí metody <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Viz také:

- [Ukázka InvokePattern, ExpandCollapsePattern a TogglePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
