---
title: Čítače výkonu služby
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 929ddcb2f271b7488270ea39e7a3a0037158c855
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320031"
---
# <a name="service-performance-counters"></a><span data-ttu-id="99733-102">Čítače výkonu služby</span><span class="sxs-lookup"><span data-stu-id="99733-102">Service Performance Counters</span></span>
<span data-ttu-id="99733-103">Čítače výkonu služby měří chování služby jako celku a dají se použít k diagnostice výkonu celé služby.</span><span class="sxs-lookup"><span data-stu-id="99733-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="99733-104">Lze je najít v objektu výkonu @no__t 0 při zobrazení pomocí nástroje Performance Monitor (Perfmon. exe).</span><span class="sxs-lookup"><span data-stu-id="99733-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="99733-105">Instance jsou pojmenovány pomocí následujícího vzoru:</span><span class="sxs-lookup"><span data-stu-id="99733-105">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> <span data-ttu-id="99733-106">Délka názvu instance čítače výkonu je omezena.</span><span class="sxs-lookup"><span data-stu-id="99733-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="99733-107">Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="99733-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99733-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99733-108">See also</span></span>

- [<span data-ttu-id="99733-109">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="99733-109">Performance Counters</span></span>](index.md)
