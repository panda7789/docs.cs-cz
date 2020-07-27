---
title: Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích
description: Podívejte se na příklad implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta v aplikaci. Všimněte si, že se jedná o neobvyklý scénář.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: c604b68021886abdf06360bfb8afefe3640c12fe
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164124"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="a8112-104">Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích</span><span class="sxs-lookup"><span data-stu-id="a8112-104">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
> <span data-ttu-id="a8112-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a8112-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a8112-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="a8112-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a8112-107">Toto téma obsahuje příklad kódu, který ukazuje, jak implementovat zprostředkovatele automatizace uživatelského rozhraní na straně klienta v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8112-107">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="a8112-108">Toto je neobvyklý scénář.</span><span class="sxs-lookup"><span data-stu-id="a8112-108">This is an uncommon scenario.</span></span> <span data-ttu-id="a8112-109">Nejčastěji se klientská aplikace automatizace uživatelského rozhraní používá pro poskytovatele na straně serveru nebo poskytovatele na straně klienta, kteří se nacházejí v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="a8112-109">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8112-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8112-110">Example</span></span>  
 <span data-ttu-id="a8112-111">Následující příklad kódu implementuje jednoduchého poskytovatele pro okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="a8112-111">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="a8112-112">Kód nemá žádné užitečné funkce, ale je určen k předvedení základních kroků při nastavování poskytovatele v rámci kódu klienta a jeho registraci pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A> .</span><span class="sxs-lookup"><span data-stu-id="a8112-112">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="a8112-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8112-113">See also</span></span>

- [<span data-ttu-id="a8112-114">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8112-114">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="a8112-115">Registrace sestavení zprostředkovatele na straně klienta</span><span class="sxs-lookup"><span data-stu-id="a8112-115">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="a8112-116">Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="a8112-116">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="a8112-117">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="a8112-117">Client-Side UI Automation Provider Implementation</span></span>](client-side-ui-automation-provider-implementation.md)
