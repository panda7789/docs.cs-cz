---
title: Čítače provozního výkonu
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 46b7d5ff071ebf1e3f790a9b56906d9908028ae9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804414"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="d9eb6-102">Čítače provozního výkonu</span><span class="sxs-lookup"><span data-stu-id="d9eb6-102">Operation Performance Counters</span></span>
<span data-ttu-id="d9eb6-103">Čítače provozního výkonu se nacházejí v části `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="d9eb6-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="d9eb6-104">Každá operace má jednotlivé instance.</span><span class="sxs-lookup"><span data-stu-id="d9eb6-104">Each operation has an individual instance.</span></span> <span data-ttu-id="d9eb6-105">To znamená Pokud danou zakázku má 10 operace, 10 instancí čítače operace jsou přidruženy k této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d9eb6-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="d9eb6-106">Instance objektů jsou pojmenované pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="d9eb6-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="d9eb6-107">Tento čítač umožňuje měření využití volání a jak dobře fungují operaci.</span><span class="sxs-lookup"><span data-stu-id="d9eb6-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d9eb6-108">Je limit na délka názvu instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="d9eb6-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="d9eb6-109">Pokud název instance čítače Windows Communication Foundation (WCF) překračuje maximální délku, WCF část název instance nahradí hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="d9eb6-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9eb6-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9eb6-110">See Also</span></span>  
 [<span data-ttu-id="d9eb6-111">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="d9eb6-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
