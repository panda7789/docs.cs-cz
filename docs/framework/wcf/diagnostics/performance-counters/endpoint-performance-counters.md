---
title: Čítače výkonu koncového bodu
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 8354cff600f8c16a5ab9b4f6efd3c0b93a46276c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="ed137-102">Čítače výkonu koncového bodu</span><span class="sxs-lookup"><span data-stu-id="ed137-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="ed137-103">Čítače výkonu koncového bodu zachytit data, která zjistí, jak koncový bod přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="ed137-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="ed137-104">Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="ed137-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="ed137-105">Instance jsou pojmenované pomocí tohoto vzoru:</span><span class="sxs-lookup"><span data-stu-id="ed137-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="ed137-106">Data je podobná shromážděné pro jednotlivé operace, ale je pouze agregován přes koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ed137-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ed137-107">Je limit na délka názvu instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="ed137-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="ed137-108">Pokud název instance čítače Windows Communication Foundation (WCF) překračuje maximální délku, WCF část název instance nahradí hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="ed137-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed137-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed137-109">See Also</span></span>  
 [<span data-ttu-id="ed137-110">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="ed137-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
