---
title: 'Služba: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 5431144a4618b146a10dfaa3bbdaae34c519319e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315782"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="024d7-102">Služba: Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="024d7-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="024d7-103">Název čítače: počet nezdařených volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="024d7-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="024d7-104">Popis</span><span class="sxs-lookup"><span data-stu-id="024d7-104">Description</span></span>  
 <span data-ttu-id="024d7-105">Počet volání s neošetřenými výjimkami, které služba obdrží za sekundu.</span><span class="sxs-lookup"><span data-stu-id="024d7-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="024d7-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="024d7-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="024d7-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="024d7-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="024d7-108">Ve spravovaném kódu jsou výjimky vyvolány, pokud dojde k chybovým podmínkám.</span><span class="sxs-lookup"><span data-stu-id="024d7-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="024d7-109">Ve spravovaném kódu jsou výjimky vyvolány, pokud dojde k chybovým podmínkám.</span><span class="sxs-lookup"><span data-stu-id="024d7-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="024d7-110">Tento čítač se zvýší pokaždé, když v této službě dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="024d7-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024d7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="024d7-111">See also</span></span>

- [<span data-ttu-id="024d7-112">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="024d7-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
