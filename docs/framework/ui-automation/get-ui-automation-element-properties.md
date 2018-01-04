---
title: "Získání vlastností elementů automatizace uživatelského rozhraní"
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
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
caps.latest.revision: "5"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f3fcbb25fab616b60a1f60d9443af13b60f2d27a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="get-ui-automation-element-properties"></a>Získání vlastností elementů automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma ukazuje, jak načíst vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu.  
  
### <a name="get-a-current-property-value"></a>Získat aktuální hodnota vlastnosti  
  
1.  Získat <xref:System.Windows.Automation.AutomationElement> jehož vlastnosti chcete získat.  
  
2.  Volání <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, nebo načíst <xref:System.Windows.Automation.AutomationElement.Current%2A> vlastnost struktura a získat hodnotu z jednoho ze svých členů.  
  
### <a name="get-a-cached-property-value"></a>Získat hodnotu vlastnosti uloženou v mezipaměti  
  
1.  Získat <xref:System.Windows.Automation.AutomationElement> jehož vlastnosti chcete získat. Tato vlastnost musí byla zadaná v <xref:System.Windows.Automation.CacheRequest>.  
  
2.  Volání <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, nebo načíst <xref:System.Windows.Automation.AutomationElement.Cached%2A> vlastnost struktura a získat hodnotu z jednoho ze svých členů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé způsoby, jak načíst aktuální vlastnosti <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Viz také  
 [Vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
