---
title: Získání vlastností elementů automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 158ebf29bb504dd11f9e8416011226fc5846873e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043618"
---
# <a name="get-ui-automation-element-properties"></a>Získání vlastností elementů automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma ukazuje, jak načíst vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvku.  
  
### <a name="get-a-current-property-value"></a>Získat aktuální hodnotu vlastnosti  
  
1. Získejte, <xref:System.Windows.Automation.AutomationElement> jehož vlastnost se má získat.  
  
2. Zavolejte <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> nebo<xref:System.Windows.Automation.AutomationElement.Current%2A> načtěte strukturu vlastností a získejte hodnotu od jednoho z jejích členů.  
  
### <a name="get-a-cached-property-value"></a>Získat hodnotu vlastnosti uložené v mezipaměti  
  
1. Získejte, <xref:System.Windows.Automation.AutomationElement> jehož vlastnost se má získat. Vlastnost musí být zadána v <xref:System.Windows.Automation.CacheRequest>.  
  
2. Zavolejte <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> nebo<xref:System.Windows.Automation.AutomationElement.Cached%2A> načtěte strukturu vlastností a získejte hodnotu od jednoho z jejích členů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé způsoby, jak načíst aktuální vlastnosti <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Viz také:

- [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](caching-in-ui-automation-clients.md)
