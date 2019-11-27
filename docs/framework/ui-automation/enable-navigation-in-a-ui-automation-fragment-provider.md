---
title: Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: 264a24646f7a3c3b5b20e94fa0ed98a1341f8273
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435760"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="cff3b-102">Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="cff3b-102">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
> <span data-ttu-id="cff3b-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="cff3b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cff3b-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="cff3b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cff3b-105">Toto téma obsahuje příklad kódu, který ukazuje, jak povolit navigaci v poskytovateli automatizace uživatelského rozhraní pro prvek, který je v rámci fragmentu.</span><span class="sxs-lookup"><span data-stu-id="cff3b-105">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cff3b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="cff3b-106">Example</span></span>  
 <span data-ttu-id="cff3b-107">Následující příklad kódu implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pro položku seznamu v rámci seznamu.</span><span class="sxs-lookup"><span data-stu-id="cff3b-107">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="cff3b-108">Nadřazený prvek je prvek pole se seznamem a prvky na stejné úrovni jsou jiné položky v kolekci seznamu.</span><span class="sxs-lookup"><span data-stu-id="cff3b-108">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="cff3b-109">Metoda vrátí `null` (`Nothing` ve Visual Basic) pro neplatnou trasu; v tomto případě <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> a <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, protože element nemá žádné podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="cff3b-109">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="cff3b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cff3b-110">See also</span></span>

- [<span data-ttu-id="cff3b-111">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cff3b-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="cff3b-112">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="cff3b-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
