---
title: 'Koncový bod: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: fa4fc1d8a875557f1da9e54e7a05eb012e7c221c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856345"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="7b344-102">Koncový bod: Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="7b344-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="7b344-103">Název čítače: Počet nezdařených volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="7b344-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7b344-104">Popis</span><span class="sxs-lookup"><span data-stu-id="7b344-104">Description</span></span>  
 <span data-ttu-id="7b344-105">Počet volání, které mají neošetřené výjimky a tento koncový bod přijatých za sekundu.</span><span class="sxs-lookup"><span data-stu-id="7b344-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="7b344-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="7b344-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="7b344-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="7b344-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="7b344-108">Tento čítač se zvyšuje vždy, když dojde k neošetřené výjimce v tomto koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="7b344-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b344-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b344-109">See Also</span></span>  
 [<span data-ttu-id="7b344-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="7b344-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
