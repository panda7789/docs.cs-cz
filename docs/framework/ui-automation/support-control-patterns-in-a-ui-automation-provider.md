---
title: Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní
description: Pochopte, jak implementovat vzory ovládacích prvků na zprostředkovatele automatizace uživatelského rozhraní, aby klientské aplikace mohly manipulovat s ovládacími prvky a získávat z nich data.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: 82300499520be6b820b361ebdeb56bbf3716afab
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163512"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="b714c-103">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b714c-103">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="b714c-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b714c-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b714c-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="b714c-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="b714c-106">Toto téma ukazuje, jak implementovat jeden nebo více vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní, aby klientské aplikace mohly manipulovat s ovládacími prvky a získávat z nich data.</span><span class="sxs-lookup"><span data-stu-id="b714c-106">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="b714c-107">Podpora vzorů ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="b714c-107">Support Control Patterns</span></span>

1. <span data-ttu-id="b714c-108">Implementujte vhodná rozhraní pro vzory ovládacích prvků, které by měl element podporovat, například <xref:System.Windows.Automation.Provider.IInvokeProvider> pro <xref:System.Windows.Automation.InvokePattern> .</span><span class="sxs-lookup"><span data-stu-id="b714c-108">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="b714c-109">Vrátí objekt, který obsahuje implementaci každého rozhraní ovládacího prvku v implementaci<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b714c-109">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="b714c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b714c-110">Example</span></span>

<span data-ttu-id="b714c-111">Následující příklad ukazuje implementaci <xref:System.Windows.Automation.Provider.ISelectionProvider> pro vlastní seznam vlastních seznamů s jedním výběrem.</span><span class="sxs-lookup"><span data-stu-id="b714c-111">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="b714c-112">Vrátí tři vlastnosti a získá aktuálně vybranou položku.</span><span class="sxs-lookup"><span data-stu-id="b714c-112">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="b714c-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b714c-113">Example</span></span>

<span data-ttu-id="b714c-114">Následující příklad ukazuje implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> , která vrací třídu implementující <xref:System.Windows.Automation.Provider.ISelectionProvider> .</span><span class="sxs-lookup"><span data-stu-id="b714c-114">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="b714c-115">Většina ovládacích prvků pole se seznamem podporuje i další vzory, ale v tomto příkladu se vrátí odkaz s hodnotou null ( `Nothing` v Microsoft Visual Basic .NET) pro všechny ostatní identifikátory vzoru.</span><span class="sxs-lookup"><span data-stu-id="b714c-115">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="b714c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b714c-116">See also</span></span>

- [<span data-ttu-id="b714c-117">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b714c-117">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="b714c-118">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="b714c-118">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
