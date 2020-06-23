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
ms.openlocfilehash: 06bf6b5901736b87852492f48a9d8972490b8304
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903464"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="02905-103">Načítání informací nastavení z domény aplikace</span><span class="sxs-lookup"><span data-stu-id="02905-103">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="02905-104">Každá instance domény aplikace se skládá z vlastností a <xref:System.AppDomainSetup> informací.</span><span class="sxs-lookup"><span data-stu-id="02905-104">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="02905-105">Můžete načíst informace o instalaci z domény aplikace pomocí <xref:System.AppDomain?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="02905-105">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="02905-106">Tato třída poskytuje několik členů, kteří načítají konfigurační informace o doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="02905-106">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="02905-107">Můžete také zadat dotaz na objekt **AppDomainSetup** pro doménu aplikace, abyste získali informace o nastavení, které byly předány doméně při jejím vytvoření.</span><span class="sxs-lookup"><span data-stu-id="02905-107">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="02905-108">Následující příklad vytvoří novou doménu aplikace a následně vytiskne několik hodnot členů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="02905-108">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="02905-109">Následující příklad nastaví a následně načte informace o nastavení pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="02905-109">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="02905-110">Všimněte si, že `AppDomain.SetupInformation.ApplicationBase` získá informace o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="02905-110">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="02905-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="02905-111">See also</span></span>

- [<span data-ttu-id="02905-112">Programování s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="02905-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="02905-113">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="02905-113">Using Application Domains</span></span>](use.md)
