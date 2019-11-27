---
title: Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: 09b33b78ef8f0b62ef4f1e24c56faae783f1e8dc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435479"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="2d38d-102">Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích</span><span class="sxs-lookup"><span data-stu-id="2d38d-102">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
> <span data-ttu-id="2d38d-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="2d38d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2d38d-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="2d38d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2d38d-105">Toto téma obsahuje příklad kódu, který ukazuje, jak implementovat zprostředkovatele automatizace uživatelského rozhraní na straně klienta v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d38d-105">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="2d38d-106">Toto je neobvyklý scénář.</span><span class="sxs-lookup"><span data-stu-id="2d38d-106">This is an uncommon scenario.</span></span> <span data-ttu-id="2d38d-107">Nejčastěji se klientská aplikace automatizace uživatelského rozhraní používá pro poskytovatele na straně serveru nebo poskytovatele na straně klienta, kteří se nacházejí v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="2d38d-107">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d38d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d38d-108">Example</span></span>  
 <span data-ttu-id="2d38d-109">Následující příklad kódu implementuje jednoduchého poskytovatele pro okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="2d38d-109">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="2d38d-110">Kód nemá žádné užitečné funkce, ale je určen k předvedení základních kroků při nastavování poskytovatele v rámci kódu klienta a jeho registraci pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d38d-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="2d38d-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d38d-111">See also</span></span>

- [<span data-ttu-id="2d38d-112">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d38d-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="2d38d-113">Registrace sestavení zprostředkovatele na straně klienta</span><span class="sxs-lookup"><span data-stu-id="2d38d-113">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="2d38d-114">Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="2d38d-114">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="2d38d-115">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="2d38d-115">Client-Side UI Automation Provider Implementation</span></span>](client-side-ui-automation-provider-implementation.md)
