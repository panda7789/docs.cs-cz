---
title: Čítače výkonu služby
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: dc31e05f82f232095f6560c8fdd9bf75c040e2ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210409"
---
# <a name="service-performance-counters"></a><span data-ttu-id="3717e-102">Čítače výkonu služby</span><span class="sxs-lookup"><span data-stu-id="3717e-102">Service Performance Counters</span></span>
<span data-ttu-id="3717e-103">Čítače výkonu služby měření chování služby jako celek a slouží k diagnostice výkonu celou službu.</span><span class="sxs-lookup"><span data-stu-id="3717e-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="3717e-104">Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="3717e-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="3717e-105">Tyto instance jsou pojmenovány pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="3717e-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="3717e-106">Platí omezení na délku název instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="3717e-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="3717e-107">Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="3717e-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3717e-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3717e-108">See also</span></span>

- [<span data-ttu-id="3717e-109">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="3717e-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
