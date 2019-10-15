---
title: Čítače výkonu koncového bodu
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 1b0f7462fea8843bcb0a0938a8034f405f30a6fb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320505"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="67128-102">Čítače výkonu koncového bodu</span><span class="sxs-lookup"><span data-stu-id="67128-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="67128-103">Čítače výkonu koncového bodu zachytí data, která odhalí, jak koncový bod přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="67128-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="67128-104">Lze je najít v objektu výkonu `ServiceModelEndpoint 4.0.0.0` při zobrazení pomocí nástroje sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="67128-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="67128-105">Instance jsou pojmenovány pomocí tohoto vzoru:</span><span class="sxs-lookup"><span data-stu-id="67128-105">The instances are named using this pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 <span data-ttu-id="67128-106">Data jsou podobná těm, která jsou shromažďována pro jednotlivé operace, ale jsou agregována pouze v rámci koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="67128-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="67128-107">Délka názvu instance čítače výkonu je omezena.</span><span class="sxs-lookup"><span data-stu-id="67128-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="67128-108">Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="67128-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67128-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67128-109">See also</span></span>

- [<span data-ttu-id="67128-110">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="67128-110">Performance Counters</span></span>](index.md)
