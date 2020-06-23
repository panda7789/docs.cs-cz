---
title: Vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní
description: Podívejte se, jak zprostředkovatel automatizace uživatelského rozhraní může vracet vlastnosti prvku klientským aplikacím v rozhraní .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
ms.openlocfilehash: 14a42c73d1dfb942a7e60ce7a72c3a5aea2b820c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903829"
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="4a2e8-103">Vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a2e8-103">Return Properties from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="4a2e8-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4a2e8-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4a2e8-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="4a2e8-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="4a2e8-106">Toto téma obsahuje vzorový kód, který ukazuje, jak zprostředkovatel automatizace uživatelského rozhraní může vracet vlastnosti prvku klientským aplikacím.</span><span class="sxs-lookup"><span data-stu-id="4a2e8-106">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="4a2e8-107">Pro jakoukoliv vlastnost, kterou explicitně nepodporuje, musí poskytovatel vracet `null` ( `Nothing` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4a2e8-107">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="4a2e8-108">Tím se zajistí, že se [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokusy o získání vlastnosti z jiného zdroje, jako je například poskytovatel hostitelského okna.</span><span class="sxs-lookup"><span data-stu-id="4a2e8-108">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a2e8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a2e8-109">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="4a2e8-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a2e8-110">See also</span></span>

- [<span data-ttu-id="4a2e8-111">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a2e8-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="4a2e8-112">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="4a2e8-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
