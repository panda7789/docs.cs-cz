---
title: Čítače provozního výkonu
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: d4f5755129fecb62e6a4da98a2bf642c5e20f9c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077105"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="34e3a-102">Čítače provozního výkonu</span><span class="sxs-lookup"><span data-stu-id="34e3a-102">Operation Performance Counters</span></span>
<span data-ttu-id="34e3a-103">Čítače provozního výkonu se nacházejí v rámci `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="34e3a-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="34e3a-104">Každá operace má jednotlivé instance.</span><span class="sxs-lookup"><span data-stu-id="34e3a-104">Each operation has an individual instance.</span></span> <span data-ttu-id="34e3a-105">To znamená že pokud má daný kontrakt 10 operací, jsou 10 instancí čítače operace spojené s touto smlouvou.</span><span class="sxs-lookup"><span data-stu-id="34e3a-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="34e3a-106">Instance objektů jsou pojmenovány pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="34e3a-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="34e3a-107">Tento čítač umožňuje měřit využití volání a jak dobře fungují operace.</span><span class="sxs-lookup"><span data-stu-id="34e3a-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="34e3a-108">Platí omezení na délku název instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="34e3a-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="34e3a-109">Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="34e3a-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e3a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34e3a-110">See also</span></span>

- [<span data-ttu-id="34e3a-111">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="34e3a-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
