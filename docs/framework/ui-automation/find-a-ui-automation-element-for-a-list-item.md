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
ms.openlocfilehash: 2b9fb1ffe4b20074de66afe6d418a7cf5d39be0c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043718"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="a33ba-102">Hledání prvku automatizace uživatelského rozhraní pro položku seznamu</span><span class="sxs-lookup"><span data-stu-id="a33ba-102">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
> <span data-ttu-id="a33ba-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a33ba-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a33ba-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a33ba-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a33ba-105">Toto téma ukazuje, jak načíst <xref:System.Windows.Automation.AutomationElement> položku pro položku v rámci seznamu, pokud je index položky znám.</span><span class="sxs-lookup"><span data-stu-id="a33ba-105">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a33ba-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a33ba-106">Example</span></span>  
 <span data-ttu-id="a33ba-107">Následující příklad ukazuje dva způsoby, jak načíst zadanou položku ze seznamu, jeden pomocí <xref:System.Windows.Automation.TreeWalker> a druhý pomocí. <xref:System.Windows.Automation.AutomationElement.FindAll%2A></span><span class="sxs-lookup"><span data-stu-id="a33ba-107">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="a33ba-108">První technika je pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky rychlejší, ale druhá je rychlejší pro ovládací prvky Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="a33ba-108">The first technique tends to be faster for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="a33ba-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a33ba-109">See also</span></span>

- [<span data-ttu-id="a33ba-110">Získání elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a33ba-110">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
