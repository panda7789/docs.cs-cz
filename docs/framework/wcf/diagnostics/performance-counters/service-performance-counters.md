---
title: Čítače výkonu služby
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 4ce0efbeb0a1d6f2409bb976102b8ec8821d5cdc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848993"
---
# <a name="service-performance-counters"></a><span data-ttu-id="1470d-102">Čítače výkonu služby</span><span class="sxs-lookup"><span data-stu-id="1470d-102">Service Performance Counters</span></span>
<span data-ttu-id="1470d-103">Čítače výkonu služby měří chování služby jako celku a dají se použít k diagnostice výkonu celé služby.</span><span class="sxs-lookup"><span data-stu-id="1470d-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="1470d-104">Lze je najít v `ServiceModelService 4.0.0.0` objektu výkonu při zobrazení pomocí nástroje Performance Monitor (Perfmon. exe).</span><span class="sxs-lookup"><span data-stu-id="1470d-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="1470d-105">Instance jsou pojmenovány pomocí následujícího vzoru:</span><span class="sxs-lookup"><span data-stu-id="1470d-105">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> <span data-ttu-id="1470d-106">Délka názvu instance čítače výkonu je omezena.</span><span class="sxs-lookup"><span data-stu-id="1470d-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="1470d-107">Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="1470d-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1470d-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1470d-108">See also</span></span>

- [<span data-ttu-id="1470d-109">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="1470d-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
