---
title: Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: b3fda706f4f2a4aa44b3627a6e6339ef0e3acb03
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673155"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="2d4fc-102">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d4fc-102">Support Control Patterns in a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="2d4fc-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2d4fc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2d4fc-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="2d4fc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="2d4fc-105">Toto téma ukazuje, jak implementovat jednu nebo více vzorů ovládacích prvků ve zprostředkovateli automatizace uživatelského rozhraní tak, aby klientské aplikace můžou manipulace s ovládacími prvky a získání dat z nich.</span><span class="sxs-lookup"><span data-stu-id="2d4fc-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>  
  
### <a name="support-control-patterns"></a><span data-ttu-id="2d4fc-106">Podpora vzorů ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="2d4fc-106">Support Control Patterns</span></span>  
  
1.  <span data-ttu-id="2d4fc-107">Implementovat vhodné rozhraní pro vzorů ovládacích prvků, které by měly podporovat element, jako například <xref:System.Windows.Automation.Provider.IInvokeProvider> pro <xref:System.Windows.Automation.InvokePattern>.</span><span class="sxs-lookup"><span data-stu-id="2d4fc-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>  
  
2.  <span data-ttu-id="2d4fc-108">Vrátí objekt obsahující vaši implementaci rozhraní každý ovládací prvek ve vaší implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2d4fc-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>  
  
## <a name="example"></a><span data-ttu-id="2d4fc-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d4fc-109">Example</span></span>  
 <span data-ttu-id="2d4fc-110">Následující příklad ukazuje implementaci <xref:System.Windows.Automation.Provider.ISelectionProvider> pro pole s jedním výběrem vlastního seznamu.</span><span class="sxs-lookup"><span data-stu-id="2d4fc-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="2d4fc-111">Vrátí tři vlastnosti a získá aktuálně vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="2d4fc-111">It returns three properties and gets the currently selected item.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a><span data-ttu-id="2d4fc-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d4fc-112">Example</span></span>  
 <span data-ttu-id="2d4fc-113">Následující příklad ukazuje implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> , která vrátí implementaci třídy <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span><span class="sxs-lookup"><span data-stu-id="2d4fc-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="2d4fc-114">Většina ovládací prvky seznamu by podporovat další zpracování, stejně, ale v tomto příkladu odkaz s hodnotou null (`Nothing` v aplikaci Microsoft Visual Basic .NET) se vrací pro všechny ostatní identifikátory vzor.</span><span class="sxs-lookup"><span data-stu-id="2d4fc-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a><span data-ttu-id="2d4fc-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d4fc-115">See also</span></span>
- [<span data-ttu-id="2d4fc-116">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d4fc-116">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="2d4fc-117">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="2d4fc-117">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
