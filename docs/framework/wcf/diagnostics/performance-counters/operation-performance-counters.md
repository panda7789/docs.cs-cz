---
title: "Čítače provozního výkonu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c752c56fa60cd717f54a7a06d0d3be8b70e7772
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="operation-performance-counters"></a><span data-ttu-id="a5567-102">Čítače provozního výkonu</span><span class="sxs-lookup"><span data-stu-id="a5567-102">Operation Performance Counters</span></span>
<span data-ttu-id="a5567-103">Čítače provozního výkonu se nacházejí v části `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="a5567-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="a5567-104">Každá operace má jednotlivé instance.</span><span class="sxs-lookup"><span data-stu-id="a5567-104">Each operation has an individual instance.</span></span> <span data-ttu-id="a5567-105">To znamená Pokud danou zakázku má 10 operace, 10 instancí čítače operace jsou přidruženy k této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="a5567-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="a5567-106">Instance objektů jsou pojmenované pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="a5567-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="a5567-107">Tento čítač umožňuje měření využití volání a jak dobře fungují operaci.</span><span class="sxs-lookup"><span data-stu-id="a5567-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a5567-108">Je limit na délka názvu instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="a5567-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="a5567-109">Když [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] název instance čítače překračuje maximální délku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nahrazuje část název instance s hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="a5567-109">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5567-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5567-110">See Also</span></span>  
 [<span data-ttu-id="a5567-111">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="a5567-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
