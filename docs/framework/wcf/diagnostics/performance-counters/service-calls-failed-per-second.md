---
title: 'Služba: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 9cd649788e1304c68caa1bbf4b5fd27e6fc9d508
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396415"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="6f91d-102">Služba: Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="6f91d-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="6f91d-103">Název čítače: Počet nezdařených volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="6f91d-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6f91d-104">Popis</span><span class="sxs-lookup"><span data-stu-id="6f91d-104">Description</span></span>  
 <span data-ttu-id="6f91d-105">Počet volání, které mají neošetřené výjimky a tato služba přijatých za sekundu.</span><span class="sxs-lookup"><span data-stu-id="6f91d-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="6f91d-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="6f91d-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6f91d-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="6f91d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="6f91d-108">Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybě podmínek.</span><span class="sxs-lookup"><span data-stu-id="6f91d-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="6f91d-109">Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybě podmínek.</span><span class="sxs-lookup"><span data-stu-id="6f91d-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="6f91d-110">Tento čítač se zvyšuje vždy, když dojde k neošetřené výjimce v této službě.</span><span class="sxs-lookup"><span data-stu-id="6f91d-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f91d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f91d-111">See Also</span></span>  
 [<span data-ttu-id="6f91d-112">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="6f91d-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
