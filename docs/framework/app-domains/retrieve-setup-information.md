---
title: Načítání informací nastavení z domény aplikace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80c9fe6de0fca86497ffe84cd8dadf0eb8cef6c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108950"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="9f490-102">Načítání informací nastavení z domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9f490-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="9f490-103">Každá instance domény aplikace se skládá z obou vlastností a <xref:System.AppDomainSetup> informace.</span><span class="sxs-lookup"><span data-stu-id="9f490-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="9f490-104">Můžete načíst informace o nastavení z domény aplikace s využitím <xref:System.AppDomain?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="9f490-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="9f490-105">Tato třída poskytuje několik členů, které načítají informace o konfiguraci o aplikační doméně.</span><span class="sxs-lookup"><span data-stu-id="9f490-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="9f490-106">Můžete také zadávat dotazy **AppDomainSetup** objektech aplikační domény k získání informací o instalaci, který byl předán při vytvoření rovnou uložil domény.</span><span class="sxs-lookup"><span data-stu-id="9f490-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="9f490-107">Následující příklad vytvoří novou doménu aplikace a potom zobrazí několik hodnot členů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9f490-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="9f490-108">Následující příklad nastaví a získá informace o nastavení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f490-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="9f490-109">Všimněte si, že `AppDomain.SetupInformation.ApplicationBase` získá informace o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="9f490-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9f490-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f490-110">See also</span></span>

- [<span data-ttu-id="9f490-111">Programování pomocí domén aplikace</span><span class="sxs-lookup"><span data-stu-id="9f490-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="9f490-112">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="9f490-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
