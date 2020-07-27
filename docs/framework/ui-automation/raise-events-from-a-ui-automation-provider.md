---
title: Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní
description: Podívejte se na příklad, který ukazuje, jak vyvolat událost ze zprostředkovatele automatizace uživatelského rozhraní. Vyvolá událost automatizace uživatelského rozhraní v implementaci vlastního ovládacího prvku tlačítko.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 75af4d05172e2417d44f76beab486de5eb3a4ba7
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168112"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="95fc6-104">Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="95fc6-104">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="95fc6-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="95fc6-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="95fc6-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="95fc6-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="95fc6-107">Toto téma obsahuje příklad kódu, který ukazuje, jak vyvolat událost ze zprostředkovatele automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="95fc6-107">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95fc6-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="95fc6-108">Example</span></span>  
 <span data-ttu-id="95fc6-109">V následujícím příkladu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je vyvolána událost v implementaci vlastního ovládacího prvku tlačítko.</span><span class="sxs-lookup"><span data-stu-id="95fc6-109">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="95fc6-110">Implementace umožňuje klientské aplikaci pro automatizaci uživatelského rozhraní simulovat kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="95fc6-110">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="95fc6-111">Aby nedocházelo k zbytečnému zpracování, příklad zkontroluje, <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> zda mají být události vyvolány.</span><span class="sxs-lookup"><span data-stu-id="95fc6-111">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="95fc6-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="95fc6-112">See also</span></span>

- [<span data-ttu-id="95fc6-113">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="95fc6-113">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
