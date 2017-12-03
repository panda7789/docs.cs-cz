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
ms.openlocfilehash: 157f0cc5d860841940b0850ca3895f82a12d47ce
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="9b2f6-102">Čítače výkonu koncového bodu</span><span class="sxs-lookup"><span data-stu-id="9b2f6-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="9b2f6-103">Čítače výkonu koncového bodu zachytit data, která zjistí, jak koncový bod přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="9b2f6-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="9b2f6-104">Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="9b2f6-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="9b2f6-105">Instance jsou pojmenované pomocí tohoto vzoru:</span><span class="sxs-lookup"><span data-stu-id="9b2f6-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="9b2f6-106">Data je podobná shromážděné pro jednotlivé operace, ale je pouze agregován přes koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9b2f6-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="9b2f6-107">Je limit na délka názvu instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="9b2f6-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="9b2f6-108">Když [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] název instance čítače překračuje maximální délku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nahrazuje část název instance s hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="9b2f6-108">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b2f6-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b2f6-109">See Also</span></span>  
 [<span data-ttu-id="9b2f6-110">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="9b2f6-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
