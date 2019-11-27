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
ms.openlocfilehash: 3ca609551955b32ad8b63296975ce10f097d9c30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433586"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje příklad kódu, který ukazuje, jak najít prvek v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu na základě konkrétní vlastnosti nebo vlastností.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou zadány sady podmínek vlastností, které identifikují určitý prvek (nebo prvky) v zájmu <xref:System.Windows.Automation.AutomationElement> stromové struktuře. Hledání všech vyhovujících prvků je následně provedeno pomocí metody <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, která zahrnuje řadu <xref:System.Windows.Automation.AndCondition> logických operací pro omezení počtu vyhovujících prvků.  
  
> [!NOTE]
> Při hledání z <xref:System.Windows.Automation.AutomationElement.RootElement%2A>byste se měli pokusit získat pouze přímé podřízené objekty. Hledání potomků může iterovat stovky nebo dokonce tisíce prvků, což může způsobit přetečení zásobníku. Pokud se pokoušíte získat konkrétní prvek na nižší úrovni, měli byste zahájit hledání z okna aplikace nebo z kontejneru na nižší úrovni.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Viz také:

- [Ukázka položky nabídky InvokePattern a ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))
- [Získání elementů automatizace uživatelského rozhraní](obtaining-ui-automation-elements.md)
- [Používání vlastnosti AutomationID](use-the-automationid-property.md)
