---
title: "Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích"
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
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
caps.latest.revision: "6"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: ae7b478ec8d836f1e0772d81185b9bb0119c0fa8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="8e750-102">Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích</span><span class="sxs-lookup"><span data-stu-id="8e750-102">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
>  <span data-ttu-id="8e750-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8e750-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8e750-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="8e750-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8e750-105">Toto téma obsahuje ukázkový kód, který ukazuje, jak pro implementaci zprostředkovatele automatizace uživatelského rozhraní na straně klienta v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="8e750-105">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="8e750-106">Jedná se o scénář neobvyklé.</span><span class="sxs-lookup"><span data-stu-id="8e750-106">This is an uncommon scenario.</span></span> <span data-ttu-id="8e750-107">Automatizace uživatelského rozhraní klientské aplikace nejčastěji využívá zprostředkovatele na straně serveru nebo zprostředkovatele na straně klienta, které se nacházejí v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="8e750-107">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e750-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e750-108">Example</span></span>  
 <span data-ttu-id="8e750-109">Následující příklad kódu implementuje jednoduchého zprostředkovatele okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="8e750-109">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="8e750-110">Kód nemá žádné užitečné funkce, ale je určená k předvedení základní kroky v nastavení služby zprostředkovatele v rámci kód klienta a její registrací pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e750-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="8e750-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e750-111">See Also</span></span>  
 [<span data-ttu-id="8e750-112">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e750-112">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="8e750-113">Registrace sestavení zprostředkovatele na straně klienta</span><span class="sxs-lookup"><span data-stu-id="8e750-113">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)  
 [<span data-ttu-id="8e750-114">Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="8e750-114">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [<span data-ttu-id="8e750-115">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="8e750-115">Client-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
