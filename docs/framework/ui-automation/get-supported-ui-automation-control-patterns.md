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
ms.openlocfilehash: 7b194d9430f27fb85723a91f5786ed11a60bfa85
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040983"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma ukazuje, jak načíst objekty vzoru ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] z prvků.  
  
### <a name="obtain-all-control-patterns"></a>Získání všech vzorů ovládacích prvků  
  
1. Získejte, <xref:System.Windows.Automation.AutomationElement> na jejichž řídicích vzorech vás zajímáte.  
  
2. Volání <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> pro získání všech vzorů ovládacích prvků z elementu.  
  
> [!CAUTION]
> Důrazně doporučujeme, aby klient nepoužíval <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Výkon může být vážně ovlivněn, protože tato metoda volá <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> interně pro každý existující vzor ovládacího prvku. Pokud je to možné, klient by <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> měl volat pro klíčové vzory zájmu.  
  
### <a name="obtain-a-specific-control-pattern"></a>Získání konkrétního vzoru ovládacího prvku  
  
1. Získejte, <xref:System.Windows.Automation.AutomationElement> na jejichž řídicích vzorech vás zajímáte.  
  
2. Zavolejte <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> nebo<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> k dotazování na konkrétní vzor. Tyto metody jsou podobné, ale pokud se vzor nenajde, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> vyvolá výjimku a <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> vrátí `false`.  
  
## <a name="example"></a>Příklad  
 Následující příklad načte <xref:System.Windows.Automation.AutomationElement> pro položku seznamu a získá <xref:System.Windows.Automation.SelectionItemPattern> z tohoto prvku.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Viz také:

- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
