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
ms.openlocfilehash: 1200ebd42884220d2611729b87f4bf51e7a903a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446829"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="d60c1-102">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d60c1-102">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="d60c1-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="d60c1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d60c1-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="d60c1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="d60c1-105">Toto téma ukazuje, jak implementovat jeden nebo více vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní, aby klientské aplikace mohly manipulovat s ovládacími prvky a získávat z nich data.</span><span class="sxs-lookup"><span data-stu-id="d60c1-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="d60c1-106">Podpora vzorů ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d60c1-106">Support Control Patterns</span></span>

1. <span data-ttu-id="d60c1-107">Implementujte vhodná rozhraní pro vzory ovládacích prvků, které by měl element podporovat, například <xref:System.Windows.Automation.Provider.IInvokeProvider> pro <xref:System.Windows.Automation.InvokePattern>.</span><span class="sxs-lookup"><span data-stu-id="d60c1-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="d60c1-108">Vrátí objekt, který obsahuje implementaci každého rozhraní ovládacího prvku v implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d60c1-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="d60c1-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d60c1-109">Example</span></span>

<span data-ttu-id="d60c1-110">Následující příklad ukazuje implementaci <xref:System.Windows.Automation.Provider.ISelectionProvider> pro vlastní seznam s jedním výběrem.</span><span class="sxs-lookup"><span data-stu-id="d60c1-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="d60c1-111">Vrátí tři vlastnosti a získá aktuálně vybranou položku.</span><span class="sxs-lookup"><span data-stu-id="d60c1-111">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="d60c1-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d60c1-112">Example</span></span>

<span data-ttu-id="d60c1-113">Následující příklad ukazuje implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>, která vrací třídu implementující <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span><span class="sxs-lookup"><span data-stu-id="d60c1-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="d60c1-114">Většina ovládacích prvků pole se seznamem podporuje i další vzory, ale v tomto příkladu se vrátí odkaz s hodnotou null (`Nothing` v Microsoft Visual Basic .NET) pro všechny ostatní identifikátory vzoru.</span><span class="sxs-lookup"><span data-stu-id="d60c1-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="d60c1-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d60c1-115">See also</span></span>

- [<span data-ttu-id="d60c1-116">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d60c1-116">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="d60c1-117">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="d60c1-117">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
