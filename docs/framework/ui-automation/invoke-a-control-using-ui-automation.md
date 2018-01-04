---
title: "Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 76b52129c0eab30bccde02389142bee2123e64f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="invoke-a-control-using-ui-automation"></a>Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma ukazuje, jak provádět následující úlohy:  
  
-   Najít ovládací prvek, který odpovídá konkrétní vlastnost podmínky zobrazení ovládacího prvku v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu cílové aplikace.  
  
-   Vytvoření <xref:System.Windows.Automation.AutomationElement> pro každý ovládací prvek.  
  
-   Získat <xref:System.Windows.Automation.InvokePattern> objekt z libovolného [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nalezen element, který podporuje <xref:System.Windows.Automation.InvokePattern> – vzor ovládacích prvků.  
  
-   Použití <xref:System.Windows.Automation.InvokePattern.Invoke%2A> k vyvolání ovládacího prvku z obslužné rutiny klienta.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metodu <xref:System.Windows.Automation.AutomationElement> k vygenerování <xref:System.Windows.Automation.InvokePattern> objektu a vyvolání ovládacího prvku pomocí <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metoda.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Viz také  
 [Vlastnost InvokePattern a ukázkové položky nabídky ExpandCollapsePattern](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
