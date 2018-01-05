---
title: "Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 40e1c1357637678456bcee0fbbeb41ecff2766d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="504b0-102">Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="504b0-102">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="504b0-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="504b0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="504b0-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="504b0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="504b0-105">Toto téma obsahuje ukázkový kód, který ukazuje, jak k povolení navigace u zprostředkovatele automatizace uživatelského rozhraní pro element, který je v rámci fragment.</span><span class="sxs-lookup"><span data-stu-id="504b0-105">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="504b0-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="504b0-106">Example</span></span>  
 <span data-ttu-id="504b0-107">Následující příklad kódu implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> položky seznamu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="504b0-107">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="504b0-108">Nadřazeným elementem je element seznamu pole a prvků jsou ostatní položky v seznamu kolekci.</span><span class="sxs-lookup"><span data-stu-id="504b0-108">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="504b0-109">Vrátí metoda `null` (`Nothing` v jazyce Visual Basic) pro pokynů, které nejsou platné; v tomto případě <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> a <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, protože element nemá žádné podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="504b0-109">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="504b0-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="504b0-110">See Also</span></span>  
 [<span data-ttu-id="504b0-111">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="504b0-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="504b0-112">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="504b0-112">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
