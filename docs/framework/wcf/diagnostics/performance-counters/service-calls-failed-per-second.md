---
title: 'Služba: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: a043cf30fa67707aca3edf50cf23372ade5e5a42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559889"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="6cdee-102">Služba: Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="6cdee-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="6cdee-103">Název čítače: Počet nezdařených volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="6cdee-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6cdee-104">Popis</span><span class="sxs-lookup"><span data-stu-id="6cdee-104">Description</span></span>  
 <span data-ttu-id="6cdee-105">Počet volání, které mají neošetřené výjimky a tato služba přijatých za sekundu.</span><span class="sxs-lookup"><span data-stu-id="6cdee-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="6cdee-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="6cdee-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6cdee-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="6cdee-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="6cdee-108">Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybě podmínek.</span><span class="sxs-lookup"><span data-stu-id="6cdee-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="6cdee-109">Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybě podmínek.</span><span class="sxs-lookup"><span data-stu-id="6cdee-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="6cdee-110">Tento čítač se zvyšuje vždy, když dojde k neošetřené výjimce v této službě.</span><span class="sxs-lookup"><span data-stu-id="6cdee-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cdee-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cdee-111">See also</span></span>
- [<span data-ttu-id="6cdee-112">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="6cdee-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
