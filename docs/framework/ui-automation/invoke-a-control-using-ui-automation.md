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
ms.openlocfilehash: 455811b1cf5da6c71225b2c3aaf25d213b3170b1
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677250"
---
# <a name="invoke-a-control-using-ui-automation"></a>Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma ukazuje, jak provádět následující úlohy:  
  
-   Najít ovládací prvek, který odpovídá konkrétní vlastnost podmínky procházením zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu pro cílovou aplikaci.  
  
-   Vytvoření <xref:System.Windows.Automation.AutomationElement> pro každý ovládací prvek.  
  
-   Získat <xref:System.Windows.Automation.InvokePattern> objekt z libovolného [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nalezen element, který podporuje <xref:System.Windows.Automation.InvokePattern> – vzor ovládacích prvků.  
  
-   Použití <xref:System.Windows.Automation.InvokePattern.Invoke%2A> k vyvolání ovládacího prvku z obslužné rutiny události klienta.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metodu <xref:System.Windows.Automation.AutomationElement> k vygenerování <xref:System.Windows.Automation.InvokePattern> objektu a vyvolání ovládacího prvku pomocí <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metoda.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Viz také:
- [Vlastnost InvokePattern ExpandCollapsePattern a vlastnost TogglePattern vzorku](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
