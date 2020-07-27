---
title: Hledání prvku automatizace uživatelského rozhraní pro položku seznamu
description: Podívejte se na příklad, který ukazuje, jak najít prvek automatizace uživatelského rozhraní pro položku seznamu, pokud je znám index položky.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: ec6464bc0ec504fd34ed113c9bed1a54a7d4eaec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168411"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="c4d70-103">Hledání prvku automatizace uživatelského rozhraní pro položku seznamu</span><span class="sxs-lookup"><span data-stu-id="c4d70-103">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
> <span data-ttu-id="c4d70-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c4d70-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c4d70-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="c4d70-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c4d70-106">Toto téma ukazuje, jak načíst <xref:System.Windows.Automation.AutomationElement> položku pro položku v rámci seznamu, pokud je index položky znám.</span><span class="sxs-lookup"><span data-stu-id="c4d70-106">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4d70-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4d70-107">Example</span></span>  
 <span data-ttu-id="c4d70-108">Následující příklad ukazuje dva způsoby, jak načíst zadanou položku ze seznamu, jeden pomocí <xref:System.Windows.Automation.TreeWalker> a druhý pomocí <xref:System.Windows.Automation.AutomationElement.FindAll%2A> .</span><span class="sxs-lookup"><span data-stu-id="c4d70-108">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="c4d70-109">První technika je pro ovládací prvky Win32 rychlejší, ale druhá je rychlejší pro ovládací prvky Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="c4d70-109">The first technique tends to be faster for Win32 controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="c4d70-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4d70-110">See also</span></span>

- [<span data-ttu-id="c4d70-111">Získání elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4d70-111">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
