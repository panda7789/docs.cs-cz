---
title: Načítání informací nastavení z domény aplikace
description: Načtěte informace o instalaci z domény aplikace v rozhraní .NET pomocí třídy System. AppDomain nebo objektu AppDomainSetup.
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
ms.openlocfilehash: 3b7fdd302ac11caa423815483a4add38264f0910
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325668"
---
# <a name="retrieve-setup-information-from-an-application-domain"></a><span data-ttu-id="f3166-103">Načíst informace o nastavení z domény aplikace</span><span class="sxs-lookup"><span data-stu-id="f3166-103">Retrieve setup information from an application domain</span></span>

<span data-ttu-id="f3166-104">Každá instance domény aplikace se skládá z vlastností a <xref:System.AppDomainSetup> informací.</span><span class="sxs-lookup"><span data-stu-id="f3166-104">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="f3166-105">Můžete načíst informace o instalaci z domény aplikace pomocí <xref:System.AppDomain?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="f3166-105">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="f3166-106">Tato třída poskytuje několik členů, kteří načítají konfigurační informace o doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="f3166-106">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="f3166-107">Můžete také zadat dotaz na objekt **AppDomainSetup** pro doménu aplikace, abyste získali informace o nastavení, které byly předány doméně při jejím vytvoření.</span><span class="sxs-lookup"><span data-stu-id="f3166-107">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="f3166-108">Následující příklad vytvoří novou doménu aplikace a následně vytiskne několik hodnot členů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="f3166-108">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="f3166-109">Následující příklad nastaví a následně načte informace o nastavení pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f3166-109">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="f3166-110">`AppDomain.SetupInformation.ApplicationBase`Získá informace o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f3166-110">`AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f3166-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3166-111">See also</span></span>

- [<span data-ttu-id="f3166-112">Programování s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="f3166-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="f3166-113">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="f3166-113">Using Application Domains</span></span>](use.md)
