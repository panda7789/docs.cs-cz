---
title: Hledání prvku automatizace uživatelského rozhraní pro položku seznamu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 63181de26f7d8efda99d5b5d71b006cde44823a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433557"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>Hledání prvku automatizace uživatelského rozhraní pro položku seznamu
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma ukazuje, jak načíst <xref:System.Windows.Automation.AutomationElement> pro položku v rámci seznamu, pokud je index položky znám.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva způsoby, jak načíst zadanou položku ze seznamu, jeden pomocí <xref:System.Windows.Automation.TreeWalker> a druhý pomocí <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.  
  
 První technika je pro ovládací prvky [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] rychlejší, ale druhá je rychlejší pro ovládací prvky Windows Presentation Foundation (WPF).  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>Viz také:

- [Získání elementů automatizace uživatelského rozhraní](obtaining-ui-automation-elements.md)
