---
title: Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: b1da13cf5eb39a61f40848a5f199cfd39b16d7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435649"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma ukazuje, jak načíst objekty vzoru ovládacího prvku z prvků [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
### <a name="obtain-all-control-patterns"></a>Získání všech vzorů ovládacích prvků  
  
1. Získejte <xref:System.Windows.Automation.AutomationElement>, jejichž vzory ovládacích prvků vás zajímají.  
  
2. Zavolejte <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> pro získání všech vzorů ovládacích prvků z prvku.  
  
> [!CAUTION]
> Důrazně doporučujeme, aby klient nepoužíval <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Výkon může být vážně ovlivněn, protože tato metoda volá <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> interně pro každý existující vzor ovládacího prvku. Pokud je to možné, klient by měl volat <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> pro klíčové vzory zájmu.  
  
### <a name="obtain-a-specific-control-pattern"></a>Získání konkrétního vzoru ovládacího prvku  
  
1. Získejte <xref:System.Windows.Automation.AutomationElement>, jejichž vzory ovládacích prvků vás zajímají.  
  
2. Zavolá <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> k dotazování na konkrétní vzor. Tyto metody jsou podobné, ale pokud se vzor nenajde, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> vyvolá výjimku a <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> vrátí `false`.  
  
## <a name="example"></a>Příklad  
 Následující příklad načte <xref:System.Windows.Automation.AutomationElement> pro položku seznamu a získá <xref:System.Windows.Automation.SelectionItemPattern> z tohoto prvku.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Viz také:

- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
