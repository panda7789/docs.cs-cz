---
title: "Čítače výkonu koncového bodu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc5fa1b3600489cb2d5f31c263019ae5006edf65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="86394-102">Čítače výkonu koncového bodu</span><span class="sxs-lookup"><span data-stu-id="86394-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="86394-103">Čítače výkonu koncového bodu zachytit data, která zjistí, jak koncový bod přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="86394-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="86394-104">Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="86394-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="86394-105">Instance jsou pojmenované pomocí tohoto vzoru:</span><span class="sxs-lookup"><span data-stu-id="86394-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="86394-106">Data je podobná shromážděné pro jednotlivé operace, ale je pouze agregován přes koncový bod.</span><span class="sxs-lookup"><span data-stu-id="86394-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="86394-107">Je limit na délka názvu instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="86394-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="86394-108">Když [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] název instance čítače překračuje maximální délku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nahrazuje část název instance s hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="86394-108">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86394-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="86394-109">See Also</span></span>  
 [<span data-ttu-id="86394-110">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="86394-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
