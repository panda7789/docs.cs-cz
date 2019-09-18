---
title: Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 278fe16bde750e674e456b5f47d9aad29147bdd4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042818"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="8fe6f-102">Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fe6f-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="8fe6f-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8fe6f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8fe6f-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8fe6f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8fe6f-105">Toto téma obsahuje příklad kódu, který ukazuje, jak vyvolat událost ze zprostředkovatele automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8fe6f-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fe6f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fe6f-106">Example</span></span>  
 <span data-ttu-id="8fe6f-107">V následujícím příkladu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je vyvolána událost v implementaci vlastního ovládacího prvku tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8fe6f-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="8fe6f-108">Implementace umožňuje klientské aplikaci pro automatizaci uživatelského rozhraní simulovat kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8fe6f-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="8fe6f-109">Aby nedocházelo k zbytečnému zpracování, <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> příklad zkontroluje, zda mají být události vyvolány.</span><span class="sxs-lookup"><span data-stu-id="8fe6f-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="8fe6f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fe6f-110">See also</span></span>

- [<span data-ttu-id="8fe6f-111">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fe6f-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
