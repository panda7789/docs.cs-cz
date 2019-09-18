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
ms.openlocfilehash: 719ea15de135d8bbeb7bb88ea3d5b5874e30b5d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053106"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="47104-102">Načítání informací nastavení z domény aplikace</span><span class="sxs-lookup"><span data-stu-id="47104-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="47104-103">Každá instance domény aplikace se skládá z vlastností a <xref:System.AppDomainSetup> informací.</span><span class="sxs-lookup"><span data-stu-id="47104-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="47104-104">Můžete načíst informace o instalaci z domény aplikace pomocí <xref:System.AppDomain?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="47104-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="47104-105">Tato třída poskytuje několik členů, kteří načítají konfigurační informace o doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="47104-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="47104-106">Můžete také zadat dotaz na objekt **AppDomainSetup** pro doménu aplikace, abyste získali informace o nastavení, které byly předány doméně při jejím vytvoření.</span><span class="sxs-lookup"><span data-stu-id="47104-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="47104-107">Následující příklad vytvoří novou doménu aplikace a následně vytiskne několik hodnot členů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="47104-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="47104-108">Následující příklad nastaví a následně načte informace o nastavení pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="47104-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="47104-109">Všimněte si `AppDomain.SetupInformation.ApplicationBase` , že získá informace o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="47104-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="47104-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47104-110">See also</span></span>

- [<span data-ttu-id="47104-111">Programování s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="47104-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="47104-112">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="47104-112">Using Application Domains</span></span>](use.md)
