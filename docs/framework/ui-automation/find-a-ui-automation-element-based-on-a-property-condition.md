---
title: Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: a80ca015a3bed202e80a93f487d37278ed03439d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740382"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje, jak vyhledat prvek v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury podle určitou vlastnost nebo vlastnosti.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu sadu podmínek vlastností jsou uvedeny, která určují určité elementu (nebo elementy), které vás zajímají v <xref:System.Windows.Automation.AutomationElement> stromu. Vyhledání všech odpovídajících prvků je pak provede s <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metodu, která zahrnuje řadu <xref:System.Windows.Automation.AndCondition> logických operací omezit počet odpovídajících prvků.  
  
> [!NOTE]
>  Při vyhledávání z <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, pokuste se získat přímé podřízené objekty. Vyhledání potomků může iterovat stovky nebo i tisíce elementů, což může vést k přetečení zásobníku. Pokud se pokoušíte získat konkrétní elementu na nižší úrovni, měli byste začít hledání v okně aplikace nebo z kontejneru na nižší úrovni.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Viz také:
- [Vlastnost InvokePattern a ukázkové položky nabídky ExpandCollapsePattern](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
- [Získání elementů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
- [Používání vlastnosti AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md)
