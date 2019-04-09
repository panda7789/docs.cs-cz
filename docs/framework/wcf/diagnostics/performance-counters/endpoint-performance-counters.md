---
title: Čítače výkonu koncového bodu
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: f07e318e39a68e689ec484b09fa743623cfb51d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158382"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="428a0-102">Čítače výkonu koncového bodu</span><span class="sxs-lookup"><span data-stu-id="428a0-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="428a0-103">Čítače výkonu koncového bodu zaznamenávat data, která se ukáže, jak koncový bod přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="428a0-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="428a0-104">Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí nástroje Sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="428a0-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="428a0-105">Tyto instance jsou pojmenovány použití tohoto modelu:</span><span class="sxs-lookup"><span data-stu-id="428a0-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="428a0-106">Data se podobá shromážděné pro jednotlivé operace, ale pouze se agreguje přes koncový bod.</span><span class="sxs-lookup"><span data-stu-id="428a0-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="428a0-107">Platí omezení na délku název instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="428a0-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="428a0-108">Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="428a0-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="428a0-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="428a0-109">See also</span></span>

- [<span data-ttu-id="428a0-110">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="428a0-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
