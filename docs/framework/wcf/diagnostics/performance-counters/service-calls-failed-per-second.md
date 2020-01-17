---
title: 'Služba: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: e165348a71101b21fa66bd4907c43335b1e476e4
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163979"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="bd6c8-102">Služba: Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="bd6c8-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="bd6c8-103">Název čítače: počet nezdařených volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="bd6c8-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bd6c8-104">Popis</span><span class="sxs-lookup"><span data-stu-id="bd6c8-104">Description</span></span>  
 <span data-ttu-id="bd6c8-105">Počet volání s neošetřenými výjimkami, které služba obdrží za sekundu.</span><span class="sxs-lookup"><span data-stu-id="bd6c8-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="bd6c8-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="bd6c8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="bd6c8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="bd6c8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="bd6c8-108">Ve spravovaném kódu jsou výjimky vyvolány, pokud dojde k chybovým podmínkám.</span><span class="sxs-lookup"><span data-stu-id="bd6c8-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="bd6c8-109">Ve spravovaném kódu jsou výjimky vyvolány, pokud dojde k chybovým podmínkám.</span><span class="sxs-lookup"><span data-stu-id="bd6c8-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="bd6c8-110">Tento čítač se zvýší pokaždé, když v této službě dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="bd6c8-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd6c8-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd6c8-111">See also</span></span>

- [<span data-ttu-id="bd6c8-112">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="bd6c8-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
