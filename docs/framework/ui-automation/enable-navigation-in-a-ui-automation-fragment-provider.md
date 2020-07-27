---
title: Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta
description: Přečtěte si příklad, který ukazuje, jak povolit navigaci v poskytovateli automatizace uživatelského rozhraní pro prvek, který je v rámci fragmentu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: bf9e43e9d70b9191fba93e5efa4eae544196c735
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168481"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="76a18-103">Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="76a18-103">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
> <span data-ttu-id="76a18-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="76a18-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="76a18-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="76a18-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="76a18-106">Toto téma obsahuje příklad kódu, který ukazuje, jak povolit navigaci v poskytovateli automatizace uživatelského rozhraní pro prvek, který je v rámci fragmentu.</span><span class="sxs-lookup"><span data-stu-id="76a18-106">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76a18-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="76a18-107">Example</span></span>  
 <span data-ttu-id="76a18-108">Následující příklad kódu implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pro položku seznamu v rámci seznamu.</span><span class="sxs-lookup"><span data-stu-id="76a18-108">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="76a18-109">Nadřazený prvek je prvek pole se seznamem a prvky na stejné úrovni jsou jiné položky v kolekci seznamu.</span><span class="sxs-lookup"><span data-stu-id="76a18-109">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="76a18-110">Metoda vrátí `null` ( `Nothing` v Visual Basic) pokyny, které nejsou platné; v tomto případě <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> a <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild> , protože element nemá žádné podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="76a18-110">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="76a18-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="76a18-111">See also</span></span>

- [<span data-ttu-id="76a18-112">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="76a18-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="76a18-113">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="76a18-113">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
