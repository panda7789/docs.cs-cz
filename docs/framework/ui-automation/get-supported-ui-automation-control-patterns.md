---
title: "Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní"
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
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: "10"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8917890d86f059d85ad9b6a0bcf6d9a41d65585a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="get-supported-ui-automation-control-patterns"></a>Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma ukazuje, jak načíst objekty vzor ovládací prvek z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy.  
  
### <a name="obtain-all-control-patterns"></a>Získání všech vzory ovládacích prvků  
  
1.  Získat <xref:System.Windows.Automation.AutomationElement> vzorů jejichž ovládacích prvků, které zajímá.  
  
2.  Volání <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> k získání všech vzorů ovládacích prvků z elementu.  
  
> [!CAUTION]
>  Důrazně doporučujeme, klient nepoužívali <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Výkon může být vážně ohrožené jako tato metoda volá <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> interně pro každý existující vzor ovládacích prvků. Pokud je to možné, by měly volat klienta <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> klíče vzorů, které vás zajímají.  
  
### <a name="obtain-a-specific-control-pattern"></a>Získat vzor konkrétní ovládacích prvků  
  
1.  Získat <xref:System.Windows.Automation.AutomationElement> vzorů jejichž ovládacích prvků, které zajímá.  
  
2.  Volání <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> dotazu pro konkrétní vzor. Tyto metody jsou podobné, ale pokud není nalezen vzor, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> vyvolá výjimku, a <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> vrátí `false`.  
  
## <a name="example"></a>Příklad  
 Následující příklad načte <xref:System.Windows.Automation.AutomationElement> položky seznamu a získává <xref:System.Windows.Automation.SelectionItemPattern> z tohoto prvku.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Viz také  
 [Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
