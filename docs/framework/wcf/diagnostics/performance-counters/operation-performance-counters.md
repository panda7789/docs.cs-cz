---
title: Čítače provozního výkonu
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 16608132c6557f8612d42402a2cb2c49fcc29637
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566085"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="92871-102">Čítače provozního výkonu</span><span class="sxs-lookup"><span data-stu-id="92871-102">Operation Performance Counters</span></span>
<span data-ttu-id="92871-103">Čítače provozního výkonu se nacházejí v rámci `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="92871-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="92871-104">Každá operace má jednotlivé instance.</span><span class="sxs-lookup"><span data-stu-id="92871-104">Each operation has an individual instance.</span></span> <span data-ttu-id="92871-105">To znamená že pokud má daný kontrakt 10 operací, jsou 10 instancí čítače operace spojené s touto smlouvou.</span><span class="sxs-lookup"><span data-stu-id="92871-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="92871-106">Instance objektů jsou pojmenovány pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="92871-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="92871-107">Tento čítač umožňuje měřit využití volání a jak dobře fungují operace.</span><span class="sxs-lookup"><span data-stu-id="92871-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="92871-108">Platí omezení na délku název instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="92871-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="92871-109">Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="92871-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92871-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92871-110">See also</span></span>
- [<span data-ttu-id="92871-111">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="92871-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
