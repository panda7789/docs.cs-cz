---
title: Čítače výkonu služby
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: bdc68fd2b629c538c097dab4e1cf3f89b7f3a091
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810184"
---
# <a name="service-performance-counters"></a><span data-ttu-id="76d84-102">Čítače výkonu služby</span><span class="sxs-lookup"><span data-stu-id="76d84-102">Service Performance Counters</span></span>
<span data-ttu-id="76d84-103">Čítače výkonu služby měřit chování služby jako celek a umožňuje diagnostikovat provádění celou služeb.</span><span class="sxs-lookup"><span data-stu-id="76d84-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="76d84-104">Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="76d84-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="76d84-105">Instance jsou pojmenované pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="76d84-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="76d84-106">Je limit na délka názvu instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="76d84-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="76d84-107">Pokud název instance čítače Windows Communication Foundation (WCF) překračuje maximální délku, WCF část název instance nahradí hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="76d84-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d84-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="76d84-108">See Also</span></span>  
 [<span data-ttu-id="76d84-109">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="76d84-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
