---
title: 'Koncový bod: počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 9634f8a170bb2fae2f15c3f00dcabb95d512c74e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321463"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="2512e-102">Koncový bod: počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="2512e-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="2512e-103">Název čítače: počet nezdařených volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="2512e-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2512e-104">Popis</span><span class="sxs-lookup"><span data-stu-id="2512e-104">Description</span></span>  
 <span data-ttu-id="2512e-105">Počet volání s neošetřenými výjimkami, které jsou přijímány tímto koncovým bodem za sekundu.</span><span class="sxs-lookup"><span data-stu-id="2512e-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="2512e-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="2512e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2512e-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="2512e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="2512e-108">Tento čítač se zvýší pokaždé, když se v tomto koncovém bodu nachází Neošetřená výjimka.</span><span class="sxs-lookup"><span data-stu-id="2512e-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2512e-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2512e-109">See also</span></span>

- [<span data-ttu-id="2512e-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="2512e-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
