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
ms.openlocfilehash: 2474edf95bf598ba9284b5f6ac36a9e0af1317a1
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741752"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="d4c12-102">Hledání prvku automatizace uživatelského rozhraní pro položku seznamu</span><span class="sxs-lookup"><span data-stu-id="d4c12-102">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
> <span data-ttu-id="d4c12-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="d4c12-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d4c12-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="d4c12-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="d4c12-105">Toto téma ukazuje, jak načíst <xref:System.Windows.Automation.AutomationElement> pro položku v rámci seznamu, pokud je index položky znám.</span><span class="sxs-lookup"><span data-stu-id="d4c12-105">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4c12-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4c12-106">Example</span></span>  
 <span data-ttu-id="d4c12-107">Následující příklad ukazuje dva způsoby, jak načíst zadanou položku ze seznamu, jeden pomocí <xref:System.Windows.Automation.TreeWalker> a druhý pomocí <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="d4c12-107">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="d4c12-108">První technika je pro ovládací prvky Win32 rychlejší, ale druhá je rychlejší pro ovládací prvky Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d4c12-108">The first technique tends to be faster for Win32 controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="d4c12-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4c12-109">See also</span></span>

- [<span data-ttu-id="d4c12-110">Získání elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4c12-110">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
