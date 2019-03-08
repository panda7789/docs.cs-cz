---
title: Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: ac351678607be824558506f7d65a5a8f6bda5a12
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674732"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="e3a3b-102">Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3a3b-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="e3a3b-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e3a3b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e3a3b-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e3a3b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e3a3b-105">Toto téma obsahuje ukázkový kód, který ukazuje, jak vyvolat událost ze zprostředkovatele automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e3a3b-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3a3b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3a3b-106">Example</span></span>  
 <span data-ttu-id="e3a3b-107">V následujícím příkladu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událost je aktivována při provádění vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e3a3b-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="e3a3b-108">Implementace umožňuje klientské aplikaci automatizace uživatelského rozhraní pro simulaci klikněte na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e3a3b-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="e3a3b-109">Aby nedocházelo k zbytečné zpracování kontroluje v příkladu <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> chcete zobrazit, zda by měla být zvýšena události.</span><span class="sxs-lookup"><span data-stu-id="e3a3b-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="e3a3b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3a3b-110">See also</span></span>
- [<span data-ttu-id="e3a3b-111">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3a3b-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
